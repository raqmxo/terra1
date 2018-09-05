# Iké Asistencia - Infraestructura AWS-ECS

<!--
# ![logo](https://raw.githubusercontent.com/raqmxo/AWS-ECS/master/images/ecs-docker.jpg)
![logox](https://raw.githubusercontent.com/raqmxo/AWS-ECS/master/images/IkeYaabFisico.png)
-->
# Bienvenido al workshop de Infraestructra Ike

En este workshop iremos armando un ambiente de Infraestructura similar al utilizado en el proyecto YaaB. Para esto, es necesario entender el uso de diferentes tecnologías utilizadas en los ambientes de QA y Productivos. Entre otras, se cuenta con:

- Docker
  _ Contenedores
  _ Imágenes
  _ DockerFile

- Cómputo en la nube (Amazon Web Services AWS)
  _ Máquinas virtuales EC2
  _ Clusters ECS
  _ Balanceadores de Aplicaciones ALB
  _ Gateway de Applicaciones AppGW
## 1) ¡Todo acerca de containers!

Te iremos guiando sobre lo básico en containers: desde instalar y configurar docker en tu laptop, ejecutar contenedores de forma local, hasta implementarlos en AWS.

## 2) Por favor, ejecuta este workshop en el siguiente orden:

- [ ] [1. Configurar ambiente inicial](https://github.com/crancurello/containers_aws/tree/master/01-SetupEnvironment)

- [ ] [2. Crear tu primer imagen de Docker](https://github.com/crancurello/containers_aws/tree/master/02-CreatingDockerImage)

- [ ] [3. Ejecutar un contenedor en un cluster de AWS ECS -Elastic Container Service-](https://github.com/crancurello/containers_aws/tree/master/03-DeployEcsCluster)

* [4. Ejecutar un contenedor con AWS Fargate](https://github.com/crancurello/containers_aws/tree/master/04-DeployFargate)

* [5. Ejecutar un contenedor en un cluster de Kubernetes con KOPS](https://github.com/crancurello/containers_aws/tree/master/05-DeployKubernetes)

* Lab alternativo: [Trabajando con ECS y ECR](https://qwiklabs.com/focuses/3456)

```yaml
version: "3"
services:
  mysql:
    image: 'mysql:5.7.21'
    container_name: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: "Pa55word@#"
      MYSQL_DATABASE: jira
      MYSQL_USER: shjira
      MYSQL_PASSWORD: "SH7ir@J18."
    ports:
      - "3306:3306"
    volumes:
      - ~/mysql:/var/lib/mysql
    command: ['--character-set-server=utf8', '--collation-server=utf8_bin']
  jira:
    image: 'cptactionhank/atlassian-jira-software:latest'
    container_name: jira
    restart: always
    ports:
      - 8080:8080
    links:
      - mysql
    external_links:
      - mysql
```

As Kanye West said:

> We're living the future so
> the present is our past.
