---
title: "mod_jk hell - tomcat55, Apache2, mod_jk -"
date: 2008-01-11
forum: Server Platforms
---

### Post by ture_atlantis on 2008-01-11
I have installed tomcat55, Apache2 and mod_jk - though aptitude

I have created a /etc/apache2/workers.properties file:
```

worker.list=localhost
worker.localhost.port=8009
worker.localhost.host=localhost
worker.localhost.type=ajp13
worker.localhost.lbfactor=1
workers.tomcat_home=/usr/share/tomcat5.5/
workers.java_home=/usr/lib/jvm/java-1.5.0-sun/

```

I have created an /etc/apache2/sites-available/tomcat.conf file - and linked it to the sites-enabled dir:
```

# Sample mod_jk configuration
# for Apache 2
#
# for all commands/options available see the manual 
# provided in libapache-mod-jk-doc package. 

# The location where mod_jk will find the workers definitions
JkWorkersFile   /etc/apache2/workers.properties
#JkWorkersFile  /etc/libapache2-mod-jk/workers.properties

# The location where mod_jk is going to place its log file
JkLogFile       /var/log/apache2/mod_jk.log

# The log level:
# - info log will contain standard mod_jk activity (default).
# - warn log will contain non fatal error reports.
# - error log will contain also error reports.
# - debug log will contain all information on mod_jk activity
# - trace log will contain all tracing information on mod_jk activity
JkLogLevel      info


# Assign specific URLs to Tomcat. In general the structure of a 
# JkMount directive is: JkMount [URL prefix] [Worker name]

# send all requests ending in .jsp to ajp13_worker
JkMount /*.jsp localhost
# send all requests ending /servlet to ajp13_worker
JkMount /*/servlet/ localhost

# JkUnmount directive acts as an opposite to JkMount and blocks access 
# to a particular URL. The purpose is to be able to filter out the 
# particular content types from mounted context.

# do not send requests ending with .gif to ajp13_worker
#JkUnMount /servlet/*.gif ajp13_worker


# JkMount / JkUnMount directives can also be used inside <VirtualHost> 
# sections of your httpd.conf file.

```

when i start apache, there is nothing listening on port 8009 or 8180:
```

root@atlantis-laptop:/var/log/tomcat5.5# netstat -tupan |grep -i listen
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     12544/apache2       
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     12544/apache2       
tcp6       0      0 :::22                   :::*                    LISTEN     7416/sshd           

```

when i try to view a .jsp page ([http://localhost/test.jsp](http://localhost/test.jsp)) i get:
```

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
Apache/2.2.4 (Ubuntu) mod_jk/1.2.23 PHP/5.2.3-1ubuntu6.2 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at localhost Port 80

```

the mod_jk log file shows:
```

[Fri Jan 11 14:14:12 2008] [12543:38576] [info]  init_jk::mod_jk.c (2743): mod_jk/1.2.23 initialized
[Fri Jan 11 14:14:12 2008] [12544:38576] [info]  init_jk::mod_jk.c (2743): mod_jk/1.2.23 initialized
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  jk_open_socket::jk_connect.c (451): connect to 127.0.0.1:8009 failed (errno=111)
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  ajp_connect_to_endpoint::jk_ajp_common.c (876): Failed opening socket to (127.0.0.1:8009) (errno=111)
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  ajp_send_request::jk_ajp_common.c (1273): (localhost) error connecting to the backend server (errno=111)
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  ajp_service::jk_ajp_common.c (1941): (localhost) sending request to tomcat failed,  recoverable operation attempt=1
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  jk_open_socket::jk_connect.c (451): connect to 127.0.0.1:8009 failed (errno=111)
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  ajp_connect_to_endpoint::jk_ajp_common.c (876): Failed opening socket to (127.0.0.1:8009) (errno=111)
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  ajp_send_request::jk_ajp_common.c (1273): (localhost) error connecting to the backend server (errno=111)
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  ajp_service::jk_ajp_common.c (1941): (localhost) sending request to tomcat failed,  recoverable operation attempt=2
[Fri Jan 11 14:14:28 2008] [12548:38576] [error] ajp_service::jk_ajp_common.c (1953): (localhost) Connecting to tomcat failed. Tomcat is probably not started or is listening on the wrong port
[Fri Jan 11 14:14:28 2008] [12548:38576] [info]  jk_handler::mod_jk.c (2254): Service error=0 for worker=localhost

```


It seems that for some reason the mod_jk is loading, but not starting up any listening service.  Has anyone experienced this problem, or know what i am doing wrong.  Thanks in advance.

---

### Post by jfdill_2 on 2008-03-10
You still need to start up tomcat5, tomcat is what listens on port 8009 not apache2.  Port 8009 is the port of tomcat's JKCS listener, apache2 talks to that port via mod_jk.  apache2 is providing the HTTP service rather than tomcat's built-in HTTP, but tomcat is still serving the applets.

If tomcat5 is not starting up, make sure you have JDK installed (probably sun-java6-jdk) and check the value of JAVA_HOME in your tomcat setup.  If you install tomcat5 from the repos, that file would be /etc/default/tomcat5 since you installed 5.5 you may have set that up differently, maybe in the init.d script.  Also, check alternatives to see which JVM you are using as the default:

```
java -version
update-alternatives --config java
```

I'm just working through trying to set up JKCS so that I can serve applets over SSL on port 443 without having to run tomcat as root (running tomcat as root is a bad idea IMO).

---

