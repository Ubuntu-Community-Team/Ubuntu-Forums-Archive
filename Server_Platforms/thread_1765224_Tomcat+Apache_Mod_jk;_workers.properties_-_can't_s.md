---
title: "Tomcat+Apache: Mod_jk; workers.properties - can't start Apache2!"
date: 2011-05-22
forum: Server Platforms
---

### Post by TMachado on 2011-05-22
I'm using apache 2.2 and Tomcat 6. I want to setup a cluster. I've seen the tutorial from

[http://www.easywayserver.com/implementation-tomcat-clustering.htm](http://www.easywayserver.com/implementation-tomcat-clustering.htm)
and
[http://www.mulesoft.com/tomcat-clustering]("http://www.mulesoft.com/tomcat-clustering")

I put on apache2.conf (info from apache documentation, already tried many other tries)

# > Where to find workers.properties
    JkWorkersFile /etc/apache2/conf.d/workers.properties
    # Where to put jk shared memory
    JkShmFile     /var/log/httpd/mod_jk.shm
    # Where to put jk logs
    JkLogFile     /var/log/httpd/mod_jk.log
    # Set the jk log level [debug/error/info]
    JkLogLevel    info
    # Select the timestamp log format
    JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
    # Send servlet for context /examples to worker named worker1
    JkMount  /examples/servlet/* worker1
    # Send JSPs  for context /examples to worker named worker1
    JkMount  /examples/*.jsp worker1

and then on workers.properties 

workers.tomcat_home=/usr/share/tomcat6
..... 

When I try to start apache I always get 

> Invalid command 'workers.tomcat_home=/usr/share/tomcat6', perhaps misspelled or defined by a module not included in the server configuration
Action 'start' failed.


I spent all day trying a lot of different combinations. Anyone can please help?

---

