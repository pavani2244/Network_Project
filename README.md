# Network_Project
Automated Deployment and Management of Container Applications in the Cloud

The mentioned project’s goal is to fully automate a deployment of a web application employing terraform, ansible, docker and GitHub actions. In this case, the assumption is to deploy an EC2 instance on aws, install docker on it, establish a simple web application within a docker container, and then automate all the processes using a CI/CD pipe line.

project outline:

main.tf- Terraform resource descriptortemplate, setup.yml- Configure EC2 instance, inventory.ini- files having information regarding EC2 instance, ci-cd-pipeline.yml- More about GitHub action pipeline, Docker file- for creating the container for simple web page, index.html- Simple web page.

Prerequisites:

AWS account 2. Docker hub installed 3. Ansible installed 4. Github account 5. Installed Terraform.
Provision Infrastructure Stepwise:

Terraform Installation and Configuration
You can install terraform by running the command. If you want to provision EC2 instance, then use the command below in the terminal area of vs code.

commands:

aws configure ## (enter your access key and secret key) terraform init terraform apply

After executing the terraform script, You will see the ip address of the EC2 instance created on your terminal.

Use the copy-pasted ec2 instance IP address and put it in inventory.ini.

Command:

[web] XX.XX.XX.XX ansible_ssh_user=ubuntu ansible_ssh_private_key_file=/path/to/private/key.pem

Ansible bootstrap: Grab and install Ansible using the following command

Command:

ansible-playbook -i Inventory.ini setup.yml

CI/CD PIPELINE:
It is recommended to store the Dockerfile and index.html into the repository. Make sure to include docker hub credentials in the secrets of Github as DOCKER_USERNAME and DOCKER_PASSWORD. Ensure to add the private key associated with the EC2, and make it a secret in Github as EC2_SSH_PRIVATE_KEY. This CI/CD is prepared to ensure that build and push occurs to the docker hub as soon as any changes are committed to the main branch.

1.build_and_push: Automatically attempts to clean up what is most likely a massive incorrect docker installation. ANser: Otherwise tag the image with emailed dhub login. For an authenticated account, latest will work.

deploy: Continuously checks and starts the program. When the image pushes, deploys the docker container. latest is accused of housing popular software that is willing to help push the docker image.

2.docker setup: docker run –config-file creates volume for host. Whenever the host does not have a valid version of index.html, docker starts thumping the image on its own.

In the combined CI/CD process for building and sending the Docker container, there is no spying activity. This application operates independently and does not utilize programs or installers.

3.ACCESSING THE APPLICATION: Once checked that Everything is up and working, the process comes to an end by getting the EC2 instance running. You can request moderator assistance if things become overwhelming.

because of the EC2 instance IP address, an instance won’t need to map additional data assets within terraform like so. An ip configuration would be handy.
