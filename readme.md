Keycloak Patches
----

This repository contains some hotfixes for released Keycloak versions.

# Build

```
mvn clean package
```

Once the build is finished, the patched jars are available in the target folders of
the respective versioned folders, e.g.:

```
hotfix/gh-9211/keycloak-services-patch-15.0.x/target/keycloak-services-patch-15.0.2.jar
```

# Apply the patched file to a Keycloak installation
1) Stop Keycloak
2) Copy the jar
3) Start Keycloak
```
cp -v ./keycloak-services-patch-15.0.2.jar /path/to/keycloak/keycloak-15.0.2/modules/system/layers/keycloak/org/keycloak/keycloak-services/main/keycloak-services-15.0.2.jar
```

# Apply the patched file to a Docker container 
1) Stop Keycloak Docker Container
2) Copy the jar 
3) Add volume mount
4) Start Keycloak Docker Container
```
-v ./keycloak-services-patch-15.0.2.jar:/opt/jboss/keycloak/modules/system/layers/keycloak/org/keycloak/keycloak-services/main/keycloak-services-15.0.2.jar:z
```


# Apply the patched file to a Docker container in docker compose
1) Stop Keycloak Docker Compose
2) Copy the jar
3) Add volume mount
4) Start Keycloak Docker Compose
```
services:
...
  keycloak:
...
    volumes:
      - ./keycloak-services-patch-15.0.2.jar:/opt/jboss/keycloak/modules/system/layers/keycloak/org/keycloak/keycloak-services/main/keycloak-services-15.0.2.jar:z
```