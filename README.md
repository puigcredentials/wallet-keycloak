
# Introduction
Wallet Keycloak is a service that allows to build the identity provider solution for the Wallet application. It composes of the newest version of Keycloak and integrate a custom login interface, as well as a basic realm with the default user for the Wallet application

# Installation

We offer a Docker image to run the application. You can find it in [Docker Hub](https://hub.docker.com/repository/docker/puigcredentials/wallet-keycloak).

Here, you can find an example of a docker-compose.yml file to run the application with all the required services and configuration.

## Running the application
```
version: '3.8'

services:
  wallet-identity-provider:
    image: puigcredentials/wallet-keycloak:v1.0.0
    environment:
      KEYCLOAK_ADMIN: "admin"
      KEYCLOAK_ADMIN_PASSWORD: "1234"
      KC_HTTP_PORT: "9099"
      KC_DB: "postgres"
      KC_DB_URL: "jdbc:postgresql://keycloak-postgres/keycloak"
      KC_DB_URL_PORT: "5433"
      KC_DB_USERNAME: "user"
      KC_DB_PASSWORD: "1234"
    ports:
      - "9099:9099"
    links:
      - keycloak-postgres

  keycloak-postgres:
    image: postgres:latest
    restart: unless-stopped
    environment:
      POSTGRES_DB: "keycloak"
      POSTGRES_USER: "user"
      POSTGRES_PASSWORD: "1234"
    ports:
      - '5433:5432'
    volumes:
      - keycloak-postgres-data:/var/lib/postgresql/data
```

## Contribution

### How to contribute
If you want to contribute to this project, please read the [CONTRIBUTING.md](CONTRIBUTING.md) file.

## License
This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Project/Component Status
This project is currently in development.

