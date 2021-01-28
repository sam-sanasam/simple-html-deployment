# simple-html-deployment
#Here are going to deploy a simple html file in the tomcat server
#TO do so, we need developer system, git server, jenkins, ansible, and webserver
# we are goining to create  4 server in the AWS names as Developer, Jenkins, ANsible, Webserver
##############################################################################################
Jenkins Server set up:
  Step 1: connect with the putty
  step 2: install java -to able to install Jenkins,< yum install java -y >
  step 3: install jenkins 
          GO to the Jenkins website, and copy the below link to install Jenkins ( go to the respective OS)
            a. wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
            b. rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
            c. yum install jenkins
  step 4: Start the Jenkins < systemctl jenkins >
  Step 5: enabling the jenkins < systemctl enable jenkins
  step 6: GO to the browser, and hit the public ip :8080 as port
  step 7: unpack the password form Jenkins GUI using < cat /var/lib/jenkins/secrets/initialAdminPassword > in the putty sesson
  step 8: Enter the passowrd in the box and authenticate
  step 9: install suggested PlugIns
  Step 10: Set the username and password and start the Jenkins sesson.
- - - - - - - -- -------------------------------------------------------
Ansible server set up:
Step 1: First connect to the putty
Step 2: install ansible << yum install ansible>>
Step 3: add the server in the ansible 
      GO to ansible host elimentory file , vi /etc/ansible/hosts 
      >> [web]
      >> inter the webserver ip address
      save the file 
 If there are more than 1 server, then collect all the private ip adresses and add in the [web] group as above
 
 -----------------------------------------------------------------------------------------------------------------
 Webserver Set up:
 Step 1: COnnect to ythe putty
 Step 2: Install apache2 < yum install httpd -y>
 Step 3:  start the apache2 , < systemctl start httpd>
 Step 4: enable the apache1 < systemctl emable httpd >
  
 ************************************************************
 ----------------------------------------------------------
 Now we need to create the connectin between the ansible and webserver as passwordless communication
 A. Passwordless connection between the Jenkins and Ansible
 B. Passwordless connection between the Ansible and Webserver
 
 
 Steps:
  step1: generate the key at Jenkins < ssh-keygen>
  step2: copy the generated key to ansible server as root < ssh-copy-id -i root@ansibleserver private IP>
          -Before that make sure that ansible server has set the root password as < passwd root>>> enter the password>> reinter the password  >
          -GO to vim /etc/ssh/sshd_config
          - uncommented the rootpassword and change password authentification fron "no" to "yes" 
    
 
 
  
