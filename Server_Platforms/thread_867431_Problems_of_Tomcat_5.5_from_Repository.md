---
title: "Problems of Tomcat 5.5 from Repository"
date: 2008-07-22
forum: Server Platforms
---

### Post by zggame on 2008-07-22
New Note 5

Hi, I installed tomcat 5.5 on a laptop Intel T2370/1G RAM and a laptop( Ubuntu 8.0.4 32bit) and Intel PIII 1.2G/512M RAM (XUbuntu 8.0.4 32bit) by Ubuntu package tool.   It is 5.5.25.0, linux 2.6.24-19-generic, i386, JVM "1.5.0"(gcj 4.2.3).  I also put the tomcat-admin package in with all the example and admin.  Both CATALINA_BASE and CATALINA_HOME at &#65279;/usr/share/tomcat5.5.  Here are two problems I met with it

1.  I cannot get any logs in the /usr/share/tomcat5.5/logs.  I check the logging.properties in conf and it seems just fine.   The logs directory is completely empty.  It seems some configuration in the repackaging has some problems with logs.  I then downloaded the binary code from tomcat website and it works just fine for the log with both the gcj and openjdk-6.  


2.  I have some problems to set up mysql JDBCRealm, a container security.  After fixing the log, I found in the original scripting, /etc/init.d/tomcat55 can only recognize gcj and gcj has some problem to parse the mysql return.  The original scipts has no option for openjdk.  I then set openjdk as JAVA_HOME and use the downloaded tomcat, JDBCRealm works just fine.

I am new for Ubuntu and hopefully this information will be helpful for others who might have the similar problems.

---

