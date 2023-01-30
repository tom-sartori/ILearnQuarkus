# ILearnQuarkus Project

## Deploying Quarkus based Amazon Lambdas

[YouTube video followed](https://www.youtube.com/watch?v=BOvxdY8cSHw)

```shell
mvn io.quarkus:quarkus-maven-plugin:2.0.0.CR3:create \
    -DprojectGroupId=org.acme \
    -DprojectArtifactId=ILearnQuarkus \
    -DclassName="org.acme.getting.started.GreetingResource" \
    -Dpath="/hello"
cd ILearnQuarkus
```

```shell
quarkus ext --installable -s aws
quarkus ext add quarkus-amazon-lambda-http
```

```shell
quarkus dev
curl http://localhost:8080/hello
```

```shell
mvn clean install -DskipTests
```

```shell
brew tap aws/tap
brew install aws-sam-cli
sam --version
sam --help
```

```shell
sam deploy -t target/sam.jvm.yaml -g
```

```
Setting default arguments for 'sam deploy'  
=========================================  
Stack Name [sam-app]: quarkus-http  
AWS Region [eu-west-3]:   
#Shows you resources changes to be deployed and require a 'Y' to initiate deploy  
Confirm changes before deploy [y/N]: y  
#SAM needs permission to be able to create roles to connect to the resources in your template
Allow SAM CLI IAM role creation [Y/n]: y
#Preserves the state of previously provisioned resources when an operation fails
Disable rollback [y/N]: y
GettingStarted may not have authorization defined, Is this okay? [y/N]: y
Save arguments to configuration file [Y/n]: y
SAM configuration file [samconfig.toml]: 
SAM configuration environment [default]:
```

```
Previewing CloudFormation changeset before deployment
======================================================
Deploy this changeset? [y/N]: y
```

```
Successfully created/updated stack - quarkus-http in eu-west-3
```
