
# Deploying High-Availability Web Application Using AWS CloudFormation

CloudFormation script to create high availability (packaged and staged in AWS S3 Storage) into an Apache Web Server. The script contains all the configurations needed for a repeatable process so that the infrastructure can be discarded and recreated at will multiple times.

<br>

### Features

`1.`  Secure Private subnets for hosting application in two availability zones within a single region.

`2.`  Server/instance specification: 2vCPUs, 4GB RAM, 10GB disk space.

`3.`  Linux Operating System using the Ubuntu 18 distribution machine image.

`4.`  Configured for two instances in each region, with auto scaling

`5.`  Jumpbox for login to secure instance using SSH

`6.`  Application servers have outbound internet access via NAT gateway for critical OS updates and patches.

`7.`  CloudFormation reads the application code from S3 bucket while spinning up instances.

`8.`  Application servers are configured with IAM instance profile to be able to access and download application code from AWS S3 bucket.

`9.` Application code is deployed on apache web server.

`10.` Entire environment is fully virtualized in a cloud platform that can be taken down and brought back up within a short period of time. The process of creating and starting all the services, spinning up instances are automated via scripts in this repo.

`11.` Outputs loadbalancer DNS name with http prefix.

<br>

### Detailed Infrastructure Architecture

![alt text][architecture]

[architecture]: https://github.com/prasadpandari/HACloudFormation/blob/master/HAArchitecture.png "Architecture Diagram"

<br>

### How to Run

create.sh and update.sh scripts help to simplify the workflow required for creating and updating 
network and server creation.

`1.`  Create network
 network.yml -> network creation cloudformation script
 network-params.json -> Parameters for network.yml
 
 Create network by running 
 ./create.sh <some-network-name> network.yml network-params.json
eg. ./create.sh haudagram network.yml network-params.json

 Updates to network can be made by running
 ./update.sh <some-network-name> network.yml network-params.json

`2.` Create Server Infra
 servers.yml -> server creation cloudformation script
 servers-params.yml -> Parameters for servers.yml

 Create servers by running
 ./create.sh <some-server-infra> servers.yml servers-params.json
 eg. ./create.sh haudagramserver servers.yml servers-params.json
 
 Updates to server infra can be done by using update.sh script

./create.sh haudagram network.yml network-params.json

<br>

### URL and Output

Url for accessing site: 

http://hauda-LoadB-YLSC9MAS1R87-449653622.us-west-2.elb.amazonaws.com 

![alt text][Screenshot]

[Screenshot]: https://github.com/prasadpandari/HACloudFormation/blob/master/Udagram.png "Screenshot"
