# Official configurations for the docker setup of TOLERANT MPM
## The configurations for each released version can be found under tags


## Package Content

```
.
+-- config
|   +-- backend
|   |   +-- mpm-gui_config_keycloak.json  # default configuration for the frontend to retrieve from the backend  
|   +-- grafana
|   |   +-- dashboards
|   |   |   +-- dashboards.yml            # default configuration for the example dashboards
|   |   |   +-- mpm_dashboard.json        # default configuration data for the example dashboard
|   |   +-- datasources
|   |       +-- datasource.yml            # default datasource to connect with Prometheus
|   +-- keycloak
|   |   +-- import
|   |       +-- tolerant-realm.json       # an example Keycloak configuration for TOLERANT
|   +-- nginx
|   |   +-- ssl
|   |   |   +-- certs                     # folder to store the self-signed certificate for Nginx
|   |   |   +-- private                   # folder to store the private key for Nginx
|   |   +-- ssl.conf.template             # default Nginx configuration used to proxy requests between the services
|   +-- openssl
|   |   +-- docker-entrypoint.sh          # an entrypoint for the OpenSSL image to create SSL certificates
|   |   +-- Dockerfile                    # a Dockerfile to build the OpenSSL image on startup
|   +-- prometheus
|       +-- prometheus.yml                # default Prometheus configuration to collect metrics from the backend service
+-- .env                                  # a configuration file containing environment variables for Docker Compose
+-- compose.yaml                          # an example configuration for docker compose 
+-- README.md
```

## Steps to use your own identity provider

-  Make sure, that you have configured your identity provider having a client with clientId and realm matching the values of **TOLERANT_CLIENT_ID** and **TOLERANT_REALM** in the .env file
-  Remove postgres and keycloak from the compose.yml, this includes **services**, **volumes** and **depends_on** sections.
-  Adjust **IDENTITY_PROVIDER_URL** and **KC_PORT** in the .env file to the URL of your identity provider and on which port it is running.