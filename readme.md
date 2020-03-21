For .Net Core projects you may need to install the global tool for SonarQube.

```bash
dotnet tool install --global dotnet-sonarscanner
```

Then, for the proper build, you should generate a token for your project and run the build as follows:

```bash
dotnet clean && \
    SONARQUBE_PROJECT="Sample" && \
    SONARQUBE_URL="http://localhost:9000" && \
    SONARQUBE_LOGIN="01122ddde9dd1ddb0c4031fcf0f86b14a12843b2" && \
    dotnet sonarscanner begin /k:$SONARQUBE_PROJECT /d:sonar.host.url=$SONARQUBE_URL /d:sonar.login=$SONARQUBE_LOGIN && \
    dotnet build && \
    dotnet sonarscanner end /d:sonar.login=$SONARQUBE_LOGIN
```