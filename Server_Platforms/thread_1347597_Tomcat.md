---
title: "Tomcat"
date: 2009-12-06
forum: Server Platforms
---

### Post by karthi_slm on 2009-12-06
hai,

      I installed tomcat6 in my system I configured my environmental variable (java_home,Path,classpath,jre_home).I started my tomcat using "sudo" command in the terminal. It goes well but when I shutdown the tomcat 
I am getting this error

Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr
6 Dec, 2009 10:13:46 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:407)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:337)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:415)

Any help would be appreciated............

---

