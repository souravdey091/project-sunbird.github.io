---
type: landing
directory: developer-docs/server-installation/
title: Configuring the Installer
page_title: Configuring the Installer
description: Prerequisites for setting up Sunbird on a server
allowSearch: true
---

## Installation Procedure

To install Sunbird Choose one docker swarm manager VM as the installation server and execute the following steps from that server. If you are installing Sunbird on two servers, execute the steps from the app server. 

## Getting the Installer

* Clone the installer repository

    git clone https://github.com/project-sunbird/sunbird-devops.git
    cd sunbird-devops
    git checkout tags/release-1.9
    cd deploy

** Description of commands:
git clone: To clone the repository on your local
cd sunbird-devops: To enter to "sunbird-devops" folder
git checkout {branch name}: To change from the current branch to tags/release branch
cd deploy: To enter to deploy folder. You can further run your git commands here

## Configuring the Installer

* Update the configuration parameters in the `config` file. 

The configuration parameters are explained in the following table: 

   | Variable Name | Description   | Mandatory|
   |-------------- |---------------|----------|
   |**ansible_private_key_path** | The path of the private SSH key file for the ssh_ansible_user. Ansible uses this file to SSH to the servers.        |yes|
   |**app_address_space**         | The application server address space. For example, 10.3.0.0/24)   |yes|
   |**backup_storage_key**| The storage key for the Elasticsearch backup |yes|
   |**badger_admin_email**| The email ID of the badger administrator |yes| 
   |**badger_admin_password**| The password for the badger administrator |yes| 
   |**cassandra_host**|The IP address of the Cassandra database.|no|
   |**cert_path**| Path to the .cert file in the SSL certificate for nginx. This variable is not mandatory, if the value of the **proto** variable is set to http.|no|
   |**database_host**|The private IP address of the DB server|no|
   |**database_password**       |  The common password for all the databases |no|
   |**dns_name**    | The domain name or IP address of your installation. Provide the IP address, if want to access Sunbird over a network or if you do not have a domain name.     |yes|
   |**ekstep_api_base_url**| The base URL for all EkStep APIs. The URL for staging is: https://qa.ekstep.in/api and production is: https://api.ekstep.in|yes|
   |**ekstep_api_key**|The JWT token generated by the key,secret produced from Ekstep |yes|
   |**ekstep_proxy_base_url**|The proxy URL for EkStep. The URL for staging is: https://qa.ekstep.in  and production: https://community.ekstep.in |yes|
   |**elasticsearch_host**       |A comma-separated (,) list of Elasticsearch database IP addresses. |no|
   |**env**    | The environment name being deployed. For example; development, test, staging, production, etc. |yes|
   |**grafana_admin_password**| password for grafana dashboard |no|   
   |**implementation_name** | Name of your sunbird implementation.|yes|   
   |**keycloak_admin_password** |The Keycloak admin console password. The default admin username is **admin**. You can change it from the Keycloak GUI   |yes|
   |**keycloak_host** | A comma-separated (,) list of Keycloak IP addresses    |no|
   |**key_path** | Path to .key file  in the SSL certificate for nginx. This variable is not mandatory, if the value of the **proto** variable is set to http |no|
   |**mail_server_host**| The ID of the mail server host used to send alerts |no|   
   |**mail_server_port**| mail server port used by mail server for alerting  |no|   
   |**mail_server_password**| password of mail |no| 
   |**mail_server_username**| username of mail |no| 
   |**monitor_alerts_slack_channel**| list of emails to send alerts |no| 
   |**monitor_alerts_slack_url**| slack app webhook url  |no| 
   |**postgres_master_host**| The IP address of the Postgres master database   |no|
   |**postgres_slave_host**| The IP address of the Postgres slave database. If you do not need a slave node, specify the IP address of the master |no| 
   |**proto**| The protocol to be used. This is either http or https. Use http if the value of the **dns_name** variable is an IP address or if you have a domain but do not want SSL for trials.yes|
   |**proxy_prometheus**| Setting up Prometheus Proxy |no| 
   |**ssh_ansible_user**  | The SSH user name that has sudo access to all servers.      |yes|
   |<a href="developer-docs/configuring_sunbird/sso_publickey" target="_blank">**sso_password</a> |The password for the keycloak SSO user. The default user is **user-manager**. You can change it from the Keycloak GUI|yes|
   |**swarm_manager_host** |A comma-separated (,) list of the IP addresses of swarm managers |no|
   |**swarm_node_host** | A comma-separated (,) list of swarm node IP addresses |no| 
   |**sunbird_azure_storage_account**  | The Azure storage account for the badger service     |yes|
   |**sunbird_azure_storage_key**  | The Azure storage key for the badger service    |yes|
   |**sunbird_default_channel**| channel name with which you are creating the organization |yes| 
   |**sunbird_image_storage_url**| The Azure image url for the badger service |yes|
   |**sunbird_installation_email**| The Sunbird installation email ID |no|
   |**sunbird_telemetry_pdata_id**| The Sunbird telemetry pdata ID, for example <br> {env}.{implimentation_name}.learning.service |no| 
   | **sudo_passwd**       |The sudo password. If the ansible user has one, the value should be specified here. The sudo password should be the same for all servers. Else, the parameter can be blank|no|  
   |**sunbird_sso_publickey**| For creation of User, http://<dns_name>/auth -> realm settings -> keys -> public keys (click on public keys) and paste the value |yes|  
   |**trampoline_secret**|The trampoline secret for Keycloak. The secret must be a minimum of 8 characters   |no|
   |**vault_postgres_exporter_password**| postgres vault exporter password |no|  
   |**vault_proxy_prometheus_admin_creds**| prometheus admin password |no|    




