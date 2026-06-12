---
title: "permission denied: port 80 tomcat"
date: 2008-06-25
forum: Server Platforms
---

### Post by eajacob on 2008-06-25
i am trying to sun tomcat web server on port 80, and the log file for the tomcat is saying permission denied: port 80. if i am running it on port 8080 no broblem, the server runs. i have ran the netstat command and no service is using the port 80. i am using the script under sudo. is there a file that reserve ports. i have installed and removed the web application for the samba server. any ideas? thanks.

---

### Post by John.Klockenkemper on 2008-06-25
You will need to provide more information regarding both tomcat and apache, with configuration files for each to get a better response regarding your problem. 

Instead of leaving it at that, I have provided you with some links to methods of running tomcat on port 80.

[http://www.klawitter.de/tomcat80.html](http://www.klawitter.de/tomcat80.html)

[http://www.mooreds.com/wordpress/archives/000295](http://www.mooreds.com/wordpress/archives/000295)

[http://esupport.marvinsweb.net/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=138](http://esupport.marvinsweb.net/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=138)

All of these articles were found by googling "Running Tomcat on Port 80"

---

### Post by lajosd on 2011-08-10
The authbind software allows a program that would normally require superuser privileges to access privileged network services to run as a non-privileged user. This article discusses how to install and configure it: [http://java-notes.com/index.php/installing-tomcat-with-http-port-80-on-linux]("http://java-notes.com/index.php/installing-tomcat-with-http-port-80-on-linux")

---

