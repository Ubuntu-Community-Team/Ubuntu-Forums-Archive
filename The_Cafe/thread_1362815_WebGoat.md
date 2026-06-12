---
title: "WebGoat"
date: 2009-12-23
forum: The Cafe
---

### Post by duleep on 2009-12-23
how to work with **WebGoat in ubuntu **[http://www.owasp.org/index.php/WebGoat_Installation#Installing_to_Linux](http://www.owasp.org/index.php/WebGoat_Installation#Installing_to_Linux)
that i used for install webgoat in ubutu
web browser see
 [html]
**Forbidden**

 You don't have permission to access /WebGoat/attack on this server.
[/html]
but running webgoat with server

> duleep@duleep-desktop:/opt/lampp/htdocs/WebGoat-5.3_RC1$ sudo sh webgoat.sh stopUsing CATALINA_BASE:   ./tomcat
Using CATALINA_HOME:   ./tomcat
Using CATALINA_TMPDIR: ./tomcat/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun-1.6.0.15/bin/../
Using CLASSPATH:       ./tomcat/bin/bootstrap.jar
duleep@duleep-desktop:/opt/lampp/htdocs/WebGoat-5.3_RC1$ sudo sh webgoat.sh start80
Using CATALINA_BASE:   ./tomcat
Using CATALINA_HOME:   ./tomcat
Using CATALINA_TMPDIR: ./tomcat/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun-1.6.0.15/bin/../
Using CLASSPATH:       ./tomcat/bin/bootstrap.jar

  Open [http://127.0.0.1/WebGoat/attack](http://127.0.0.1/WebGoat/attack)
  Username: guest
  Password: guest
  Or try [http://guest:guest@127.0.0.1/WebGoat/attack](http://guest:guest@127.0.0.1/WebGoat/attack) 

    at org.apache.catalina.core.StandardServer.start(StandardServer.java:700)
    at org.apache.catalina.startup.Catalina.start(Catalina.java:552)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:295)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:433)
Dec 24, 2009 2:27:13 AM org.apache.catalina.startup.Catalina start
INFO: Server startup in 717 ms

plz tell me how to run webGoat

---

