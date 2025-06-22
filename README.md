##############################
# Linux-fundamentals-vagrant #
##############################

This project describe Basic Linux system administration tasks using Vagrant and virtualbox on windows

Table of Content
a. requirement
1. install virtualbox
2. install vagrant
-- SSH into vagrant Server
3.Exploring the Linux File System in the vagrant
4. Managing File Permissions and Ownership
5. Install and Configure a Package
6. Testing Remote Connectivity from vagrant box
   
#Softwares required 1. virtualbox, 2. vagrant 3. CLI
#### Note -----there are issues related to the version of virtualbox that works with certain version of vagrant, hence you can check online for which version is suitable for your virtualbox. e.g this project uses virtualbox 7.0.26 and vagrant 2.3.7

1. How to setup virtualbox
    ---use this link to download virtualbox : https://www.virtualbox.org/wiki/Downloads
    ---specify the version of choice
    ---accept license agreement to complete installation

2. Setup Vagrant Server (either windows or Linux)
    ---use this link to download vagrant : https://developer.hashicorp.com/vagrant/docs/installation
    ---specify the version of choice
    ---accept license agreement to complete installation
    ---Once done, Open any CLI e.g powershell, cmd, git cmd  
    ---verify vagrant using cmd $vagrant --version

#####----For this project GIT CMD is used----#####
Below commands are used to create and initialized the vm box   #Vagrant boxes https://developer.hashicorp.com/vagrant/vagrant-cloud/boxes/catalog

1. $vagrant box add ubuntu/focal64
![vagr1](https://github.com/user-attachments/assets/268559a8-010f-4e95-bb4b-cd4365051bb4)

2. $vagrant init ubuntu/focal64
   ![vagr2](https://github.com/user-attachments/assets/a7082f18-47e6-49bd-862c-168a80419e73)

3. $vagrant plugin install vagrant-vbguest
![vagr3](https://github.com/user-attachments/assets/63692af8-f558-416e-88f3-d0b7370862c7)

4. $vagrant up
![vagr5](https://github.com/user-attachments/assets/001a8d90-c4cd-405c-9b70-873582dd3488)
![vagr4](https://github.com/user-attachments/assets/14bfbc7c-3fe0-48aa-b501-28835b930890)
![vagr6](https://github.com/user-attachments/assets/f8aec545-5388-4140-81c5-d378a9b4193e)


#SSH into vagrant Server
 $vagrant ssh
![vagr7 ssh](https://github.com/user-attachments/assets/bd7f6c8e-fe06-4159-85a7-ae7c9c304fc5)
#The above cmd grant acces to the vm box,  username: vagrant, password: vagrant

3. Exploring the Linux File System in the vagrant vm box ----use below cmd
vagrant@ubuntu-focal:$ ls -l   #this cmd list files or directories in the home directory
vagrant@ubuntu-focal:$ pwd     #this cmd display the path to home directory/home/vagrant
vagrant@ubuntu-focal:$ cd /    #this cmd change directory to the root
   
3i. Create a custom folder structure (e.g., /home/vagrant/projects/devops).
    vagrant@ubuntu-focal:~$ mkdir -p projects/devops
 ![vagr7 custm dir](https://github.com/user-attachments/assets/bd48e317-192e-49a8-b069-c33c9dbdf1d5)
--This command creates first diretory "projects", there after created another one "devops" inside the projects directory.

4. Managing File Permissions and Ownership
--In Linux, permissions and ownership control who can access or  modify files and directories; Ownership refers to who "owns" a file. Each file has:
a user owner (usually the creator)
a group owner (used to grant access to a set of users)

#Permissions define what actions those users or groups can take. There are three types:
r (read): can view the file contents
w (write): can modify the file
x (execute): can run the file as a program or access a directory

Create files and use chmod and chown 
#this cmd create two empty files simultaneously
 vagrant@ubuntu-focal:~$ touch file-example1.txt fileexample2.txt
 ![vagr txtcrt](https://github.com/user-attachments/assets/829cdc2b-2c7b-4068-91a0-9d59005c185c)
 
#this cmd make the file executable 
vagrant@ubuntu-focal:~$ chmod +x file-example1.tx
![vagr txtpmchange](https://github.com/user-attachments/assets/2183e0ce-84a9-40ab-989b-3d39a624522f)

#this cmd changes both the user and group of the created files
vagrant@ubuntu-focal:~$sudo chown root file-example1.txt
vagrant@ubuntu-focal:~$sudo chown root:root file-example2.txt
![vagr chown2](https://github.com/user-attachments/assets/c364d662-ed72-4818-a2b9-9ebdfc538657)


5. Install and Configure a Package
#----Lets Install a basic package with vagrant box  use below cmd
 vagrant@ubuntu-focal:~$ sudo apt install apache2

![vagr7 pack](https://github.com/user-attachments/assets/7ba44d09-f9b9-413a-8eb2-78e4a10e16a4)
![vagr7 pack2](https://github.com/user-attachments/assets/2ae84ffa-401b-47f3-bf94-0d2d5fb5e623)
![vagr7 pack3](https://github.com/user-attachments/assets/1eb927d3-cded-4f3b-bcd1-48e9b7975ffc)

6. Test Remote Connectivity from vagrant box
-----Use ping to test connectivity to a remote server .
vagrant@ubuntu-focal:ping -c google.com
vagrant@ubuntu-focal:ping -c facebook.com
![vagr remote](https://github.com/user-attachments/assets/de2fff0b-d732-46b4-b8fb-be9a239ccead)

