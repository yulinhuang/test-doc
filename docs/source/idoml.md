# IDOML server configuration repository
Welcome to IDOML server repo!

In this repository you will find the configuration files to deploy the IDOML server. The IDOML server is a docker-compose based deployment of the following services:
- Airflow
  - Git-sync
- Minio
- Keycloak
- Traefik


## Requirements
1. Hardware Requirements:

    - A Linux server with a minimum of 8GB of RAM and 4 CPU cores is required to run the platform efficiently. This configuration ensures optimal performance and scalability for your machine learning tasks.

    - Note that the above requirement is exclusive of resources needed for hosting a JupyterHub server and executing machine learning tasks. The resources for JupyterHub server hosting vary based on the number of users and the size of data they handle. Similarly, resources for machine learning tasks depend on task complexity and data size. Scaling up for ML tasks can be achieved by hosting additional servers to manage [airflow workers](https://github.com/serval-uni-lu/idoml-worker-node).

3. Before deploying IDOML, update the **.env** file with the necessary configurations:
    - Domain name Configuration:

        We expect that the user dispose a custom domain name. Please redirect all the subdomains to the server's IP address.
        Then update the **.env** file with the variable IDOML_DOMAIN. This domain will be used to access the services deployed on the server.

    -   Credentials setup:

        Please update the credential settings section of the **.env** file.

## Configuration after deployment

### MINIO

    
#### Generate credentials for airflow
    
```
docker-compose exec minio sh -c "mc admin user add minio airflow ${MINIO_ROOT_PASSWORD} readwrite
```
 -->
