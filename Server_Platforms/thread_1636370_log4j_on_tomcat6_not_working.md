---
title: "log4j on tomcat6 not working"
date: 2010-12-03
forum: Server Platforms
---

### Post by Daribo on 2010-12-03
Hi,

I am running tomcat6 and java 1.6. I want to log my spring application, but outside of /var/logs/tomcat6/. My OS is Ubuntu 10.10.

I am simply trying to create a log file ('mylog.log') and store it inside my webapp application. Unfortunately, it doesn't do anything....

Here is my log4j.properties:
[PHP]
log4j.rootLogger = INFO, rollingFile
log4j.appender.rollingFile=org.apache.log4j.RollingFileAppender
log4j.appender.rollingFile.File=/home/daribo/webapps/helloworld/mylog.log
log4j.appender.rollingFile.MaxFileSize=2MB
log4j.appender.rollingFile.MaxBackupIndex=2
log4j.appender.rollingFile.layout = org.apache.log4j.PatternLayout
log4j.appender.rollingFile.layout.ConversionPattern=%p %t %c - %m%n
[/PHP]I even set the permission of the helloworld directory to 777 so that everybody can write or delete it. (It's only for my use).

If I restart tomcat, I don't see any log file being created.

I appreciate any hints!

---

