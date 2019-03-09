## An introduction to Ansible
Ansible is an agentless configuration tool that works over SSH.

### Key concepts
1. Modules  
Ansible has many built in modules to configure a wide range of tools, there are the basic building block in Ansible. E.g. configuring mysql with mysql_db; installing python packages with pip.

1. Roles  
While modules are great, they functionally do a single thing. E.g. Add a user to mysql. Usually, we want to do a logical tasks, called a role. Using the mysql example, a role could be installing mysql, starting it and adding the admin user. A second role could be preparing clients for connecting to that mysql server by installing python-mysqldb.

1. Inventories  
Inventories are where groups are configured for controlled machines. An example would be:
[NTP_server]  
192.168.1.1  
[NTP_client]  
192.168.1.[2-4]  
[mysql_server]  
192.168.1.1  
[mysql_client]  
192.168.1.4  

1. Playbooks  
Roles contain the tasks to be done, inventories define the systems to be configured. Putting them together are playbooks. Playbooks define what roles are assigned to which group. Using the mysql example again, I would want the install mysql role to be executed on mysql\_server and the client roles to be executed on mysql\_client.

1. Variables  
Ansible supports variables, on a per host basis. Imagine a config file where you need to specify your own MAC address, per host variables allows this. It also allows global variables, such as pointing to a common NTP server on multiple servers. Variables can be configured in many locations.

1. Idempotence  
A key aspect of Ansible is that playbooks should be idempotent. What this means is that, once a playbook has been run, and the system has went from state 0 to state 1, rerunning the playbook will not change the state further.

### Prerequisites
1. Control machine requires python 2.7/3.5 and above. Windows is not supported.
1. Managed node requires SSH access, and python binaries should be available at /usr/bin/python. (-raw parameter can be used to install python)
1. Sudo privileges are usually needed for configuration, thus the sudo password should be known. Sensitive details can be stored in Ansible Vault.

### Best practices
1. Directory structure

### Examples
1. Install packages
1. Setup python environment
1. Generate and push configurations
1. Update os
