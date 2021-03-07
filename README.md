# ec2_provision_with_nginx_static_webhosting
Ansible playbook with creation of ec2 instance and installing nginx(and static web hosting using nginx)

Before executing the playbook, 
please create the ansible vault file for storing the aws access_key and secret_key(with password protection)

steps:
Create Ansible Vault file (within current directory)to store the AWS Access and Secret keys.
**ansible-vault create group_vars/all/pass.yml
New Vault password:<put_ur_password>
Confirm New Vault password:<put_ur_password>

If you want to edit vault file, then please follow below step

Edit the pass.yml file and create the keys global constants

ansible-vault edit group_vars/all/pass.yml 
Vault password:
ec2_access_key: AAAAAAAAAAAAAABBBBBBBBBBBB                                      
ec2_secret_key: afjdfadgf$fgajk5ragesfjgjsfdbtirhf


finally, execute below command to run playbook

ansible-playbook -i hosts 1_ec2_provision.yml --ask-vault-pass (hit enter)

it will asks passwd for vault file(which has set in above step). Just enter the password, then it will execute the playbook.

After execution,

it will upload ssh key file to aws(which is present at "/home/<username>/.ssh/" directory.
after that it will create security group with ports 80 and 22 allowed.
create new ec2 instance and attach above key par to it.

Installs nginx and serve the status index.html page content over public url.
  


