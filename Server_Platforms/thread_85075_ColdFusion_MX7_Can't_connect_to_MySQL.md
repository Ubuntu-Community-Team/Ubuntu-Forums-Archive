---
title: "ColdFusion MX7: Can't connect to MySQL"
date: 2005-11-01
forum: Server Platforms
---

### Post by ytseshred on 2005-11-01
I have successfully installed the developers edition of ColdFusion MX 7 on my ubuntu server.  I can correctly log into the ColdFusion administrator, but when I try to add a datasource to connect to MySQL (on the same ubuntu machine), I get the following error:
```
 Connection verification failed for data source: facultyworx_dev
java.sql.SQLException: Timed out trying to establish connection
The root cause was that: java.sql.SQLException: Timed out trying to establish connection
```

I found some instructions that said to manually make sure the proper Connector class was installed.  I installed the newest MySQL Connector/J in /usr/local/addons on my server.
The full path to it reads:```
/usr/local/addons/mysql-connector-java-3.1.11
```

The instructions I had found said to put the .jar file from the above mysql-connector folder into the /lib directory of the ColdFusion folder.  So I put 

mysql-connector-java-3.1.11-bin.jar into the ColdFusion folder.  I then also clicked on the "Java and JVM" section in the ColdFusion administrator, and put this in the "ColdFusion Class Path" section:
/opt/coldfusionmx7/lib/mysql-connector-java-3.1.11-bin.jar

I restarted the server, but I still get the same error.  Does anyone have any experience manually installing an appropriate JDBC Connector for ColdFusion on Ubuntu?  Any help would be appreciated.  Thanks.

---

### Post by sdhoigt on 2006-07-19
I had this "problem" after installing CF 6.1 on Debian 3.1.

When adding a data source, are you using 'localhost' for the server name?  I think I had the same error as you.  In my case, I used 127.0.0.1 for the server name, and that's all it took.

Also, here's a reference I found re:CF MX 7 and MySQL set-up.  I haven't read it yet.
[http://www.howtoforge.com/coldfusion7_mysql4.1_connection](http://www.howtoforge.com/coldfusion7_mysql4.1_connection)

SD

---

