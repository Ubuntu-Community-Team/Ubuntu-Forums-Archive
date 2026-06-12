---
title: "Tomcat problem loading"
date: 2006-08-22
forum: Server Platforms
---

### Post by hogman23 on 2006-08-22
I am having problems getting Tomcat to load on my server.  Here is the log file output.  Any ideas?

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/catalina/startup/Bootstrap
Using CATALINA_BASE:   /var/lib/tomcat5
Using CATALINA_HOME:   /usr/share/tomcat5
Using CATALINA_TMPDIR: /var/lib/tomcat5/temp
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun/
Using Security Manager

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/catalina/startup/Bootstrap
Using CATALINA_BASE:   /var/lib/tomcat5
Using CATALINA_HOME:   /usr/share/tomcat5
Using CATALINA_TMPDIR: /var/lib/tomcat5/temp
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun/
Using Security Manager

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/catalina/startup/Bootstrap
Using CATALINA_BASE:   /var/lib/tomcat5
Using CATALINA_HOME:   /usr/share/tomcat5
Using CATALINA_TMPDIR: /var/lib/tomcat5/temp
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun/
Using Security Manager

---

### Post by hogman23 on 2006-08-22
Ok, I fixed the first errors, I was missing some jar files, now I'm getting this...

Using CATALINA_BASE:   /var/lib/tomcat5
Using CATALINA_HOME:   /usr/share/tomcat5
Using CATALINA_TMPDIR: /var/lib/tomcat5/temp
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun/
Using Security Manager
java.lang.ClassNotFoundException: org.apache.catalina.core.ApplicationContextFacade$1
        at org.apache.catalina.loader.StandardClassLoader.loadClass(StandardClassLoader.java:854)
        at org.apache.catalina.loader.StandardClassLoader.loadClass(StandardClassLoader.java:721)
        at org.apache.catalina.security.SecurityClassLoad.loadCorePackage(SecurityClassLoad.java:53)
        at org.apache.catalina.security.SecurityClassLoad.securityClassLoad(SecurityClassLoad.java:39)
        at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:200)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:402)

---

### Post by sagary7 on 2007-08-28
CAn you please tell me what all jar files you forgot? cos i have the same problem prevailing here. 

ThankYou,
Sagar.

---

### Post by phasnoxc on 2007-11-01
Had the same problem... The tip about the libs help

apt-get --purge remove tomcat5.5 tomcat5.5-admin libtomcat5.5-java libservlet2.4-java

apt-get install tomcat5.5 tomcat5.5-admin

Worked for me..

---

