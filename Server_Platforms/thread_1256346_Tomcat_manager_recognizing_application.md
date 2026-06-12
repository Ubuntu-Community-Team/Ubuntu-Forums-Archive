---
title: "Tomcat manager recognizing application"
date: 2009-09-02
forum: Server Platforms
---

### Post by hugh v. angle on 2009-09-02
I have run a Tomcat application on MS for three years.
I am trying to move this system to Ubuntu that I
installed two months ago.

I cannot get the Tomcat manager to recognize my
application. I created a test application with a
WEB-INF structure and placed it in the tomcat6/webapps
directory. My system has two webapps directories:
(1) /var/lib/tomcat6/webapps
(2) /usr/share/tomcat6/webapps
The '/var/lib... path seems to work. Actually,
the server displays html files from 
/var/lib/tomcat6/webapps/ROOT; so I  placed
my application there.  

I have to restart Ubuntu in order to stop and start
the server.  The /usr/share/tomcat6/bin/shutdown.sh 
script throws an  exception-- file not found:
/usr/share/tomcat6/conf/server.xml.  The server.xml
is in directory /usr/share/tomcat6/skel/conf.

Under MS, the manager recognizes a new tomcat
structure placed in the webapps directory. Somehow
I suspect that I have failed to find the proper
directory. I love my new operating system; however,
the system directories are a scary labyrinth.

I am happy with the private instance of Tomcat that
I discovered a few days ago.  I activated it with 
'tomcat6-instance-create my-instance'
It has a bin directory with shutdown.sh and startup.sh
that work and whose operations executes the reloading 
in lieu of the manager.  Also I do not have to 
contend with the webapps directory. I wish I had  had
something like this a few years ago.

---

