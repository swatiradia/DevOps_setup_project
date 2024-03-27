**Devops Project**

**DevOps -> Developement + Operations**

Its the combination of best practises and tools that increase an organizations ability to deliver software into production at highest velocity.

**Practices:** Continuous integration and Continuous delivery
**Tools:** AWS, Jenkins, Docker, Bamboo, GIT, Maven, Ansible etc

**Continuous integration:** CI is the process of automating the build and testing of code every time a member of the team commits changes to version control/GIT.

**Continuous Delivery:** CD is the process of build, test, configure and deploy from a build to production environment.

**Understanding basic deployment**

**Application Server:** An application server is a server specifically designed to run applications.
It handles http requests and sends response over http protocol.

**Hosted Server:** Hosted Servers are nothing but physical machines where application/Web/Databases servers are hosted

Apache Tomcat is a application server.

Points from the course

1. AWS ec2 instance is created to host Jenkins. The IP address of the ec2 instance is noted.
2. Once the ec2 instanec is created , its connected through a SSH client, such as putty using the IP address and the password pem file.
3. In this course MobaXterm is used for ssh connection.[All the ec2 instances are named ec2-user, this is used while ssh connection]
4. Once the connection is established, a command prompt opens.
5. ec2 instance will have two users by deafult -> es2-user and root user.
6. To setup all the files, we need to be on the root user
7. below command is used for logging into root user.
   sudo su -
8. To see hidden files. ls -a
9. To keep our Developed App running on server and access it from anywhere, we should first build the code so that build files will be generated. These build files should be placed into App/Web Server And then we can access the developed App directly on the browser with HostedServerIpAddress :portNumber or with Domain Name if mapped.
10. First Yum Tool needs to be installed on the root user.
    **Yum Tool** Yum is a command line tool used for getting, installing, deleting, querying and managing software packages.
    **Command used** sudo yum install yum
11. Next we need to install java on the ec2 istance.
    **Command used** su -c "yum install java-[version]
12. Java is installed in usr/lib directory
    Set Java Home Path in Bash profile
    JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.51.amzn1.x86_64
    PATH=$PATH:$HOME/bin:$JAVA_HOME:
13. Next install Maven on the ec2 instance.
    **wget-** Wget solely lets you download files from an HTTP/HTTPS or FTP server. You give it a link and it automatically downloads the file where the link points to. It basically helps to download Binaries
    wget <downloadlinkofMaven>
    tar xzvf <mavenfoldername>
    M2=/opt/apache-maven-3.6.3/bin
    PATH=$PATH:$HOME/bin:$JAVA_HOME:$MAVEN_HOME:$M2
    Set Maven in System variables
    JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.51.amzn1.x86_64
    MAVEN_HOME=/opt/apache-maven-3.6.3
14. Then finally install Jenkins for Continuous Integration.
    • sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins.io/redhat/jenkins.repo
    • sudo rpm --import http://pkg.jenkins.io/redhat/jenkins.io.key
    • sudo yum install jenkins
    • Start Jenkins - sudo service jenkins start/stop/restart
    • sudo chkconfig jenkins on
