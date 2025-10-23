# ansible-playbook
Ansible Setup to Ansible Playbook
## Add Ansible Repo In Your OS
```bash
sudo apt-add-repository ppa:ansible/ansible
```
```bash
sudo apt update
```
```bash
sudo apt install ansible
```
Now Confirm That Your Ansible Install Proper_Version
```bash
ansible --version
```
---
## Now Configure Your Host File:
```bash
sudo nano /etc/ansible/host
```
For example:
```bash
[servers]
server_1 ansible_host=192.168.1.10    # Your Public Ip
server_2 ansible_host=192.168.1.11    # Your Public Ip

[prod]
server_3 ansible_host=192.168.1.12    # Your Public Ip

[all:vars]  #You can use specific group name instead of all
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/ansible-key.pem

#[dbservers]
#db1.example.com
#db2.example.com
```
## Check servers Inventory List:
```bash
ansible-inventory --list -y
```
## Note:
You have to place .pem key on Master-Server workplace with
```scp -i "ansible-key.pem" ansible-key.pem ubuntu@ec2-52-90-146-24.compute-1.amazonaws.com /home/ubuntu```
Give Permission ```chmod 400 ansible-key.pem```
---
## Check All Servers Connected Via Ping
```bash
ansible all -m ping -u ubuntu
```
## Check Memory Of All Servers With Adhock CMD:
```bash
ansible all  -a "free -h"   #adhock cmd example
```
----
## Role of Ansible PlayBook
Make Dir For Playbook:
```bash
mkdir playbooks
cd playbooks
```
## Execute Your Playbook:
```bash
ansible-playbook -v date_play.yml
```
