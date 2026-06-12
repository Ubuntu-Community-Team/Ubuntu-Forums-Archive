---
title: "Problems with CLASSPATH java.lang.ClassNotFoundException: com.mysql.jdbc.Driver"
date: 2008-04-11
forum: Server Platforms
---

### Post by Ibane on 2008-04-11
Hello,

I am aware of that this might not be the right place, however I wonder if anyone could help here.

I am running Ubuntu Server dapper 6.06.2 LTS.

Hardware
Dell Pentium 4
Processor: Intel Pentium 4 (R) 3.00 GHz
cache size: 1024
Total Physical Memory: 1009,91 MB
Total Swap Memory: 753 MB

Software installed
Tomcat 6
MySQL
Java-6-sun

My CLASSPATH. CLASSPATH=/usr/lib/jvm/java-6-sun/lib/mysql-connector-java-3.1.14-bin.jar:
/usr/local/tomcat/lib/jsp-api.jar:/usr/local/tomcat/lib/servlet-api.jar

Tomcat is running without problems but when I am trying to connect to MySQL through java I get the well known
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver

Any ideas what could I be missing? Any help is appreciated.

Thanks

---

