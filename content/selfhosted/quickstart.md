---
title: "Quick Start"
order: 2
---

# Rebugit can be deployed in with:

- [Helm chart](/selfhosted/helm-chart)

- [Docker compose](/selfhosted/docker-compose)

- Containers: run the containers yourself, you can check the **Containers** section or the [Rebugit public repository](https://gallery.ecr.aws/rebugit/)


# Helm chart quick start
Deploy the chart in your Kubernetes cluster:

1. Add the Rebugit helm repository:
  ```shell
  helm repo add rebugit https://charts.rebugit.com
  ```
<br/>
2. Create a namespace if needed:
  ```shell
  kubectl create namespace rebugit
  ```
<br/>
3. Deploy the chart:
  ```shell
  helm upgrade -i rebugit -n rebugit rebugit/rebugit \
    --set rebugit.host="$APPLICATION_DOMAIN" \
    --set postgresql.postgresqlPassword="$POSTGRES_PASSWORD" \
    --set postgresql.postgresqlUserPassword="$POSTGRES_USER_PASSWORD" \
    --set keycloak.auth.adminPassword="$KEYCLOAK_ADMIN_PASSWORD" \
    --set keycloak.auth.userName="$KEYCLOAK_USER_NAME" \
    --set keycloak.auth.userPassword="$KEYCLOAK_USER_PASSWORD"
  ```


<Info>

**Note:** this chart is deployed using [Nginx ingress controller](https://kubernetes.github.io/ingress-nginx/).
If you are using another ingress controller you can modify [the ingress section of the `values.yaml`](https://github.com/rebugit/standalone/blob/master/helm/values.yaml).

</Info>

### After the deployment

Your application will be running at: `$APPLICATION_DOMAIN/rebugit/web/`,
this link will redirect you to the login page where you can input your `KEYCLOAK_USER_NAME` and `KEYCLOAK_USER_PASSWORD`.

You can now create a new project and grab the generated API key and paste it in your SDK.


### Quick variables description

| Variable                  	| Description                                                                                                                                                                              	|
|---------------------------	|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| `APPLICATION_DOMAIN`      	| The domain of your application: `myapplication.com`                                                                                                                                      	|
| `POSTGRES_PASSWORD`       	| The postgres admin password                                                                                                                                                              	|
| `POSTGRES_USER_PASSWORD`  	| The postgres user password, the user name is `app`. This user has lower privileges than the admin                                                                                        	|
| `KEYCLOAK_ADMIN_PASSWORD` 	| Keycloak is the on-premise authentication service rebugit uses, if you wish to add users and change configuration, you can log into the console using this password and username `admin` 	|
| `KEYCLOAK_USER_NAME`      	| This is the user that you can use to access the Rebugit application resources, dashboard and IDE extension                                                                               	|
| `KEYCLOAK_USER_PASSWORD`  	| The password associated to the user above                                                                                                                                                	|


For more information you can check the chart repository [visit the Github repository](https://github.com/rebugit/standalone/tree/master/helm) or check the [full documentation](/selfhosted/helm-chart)

### Sample applications

You can check some *ready to deploy* sample applications [here](https://github.com/rebugit/standalone/tree/master/samples)

---

# Docker compose

Coming soon
