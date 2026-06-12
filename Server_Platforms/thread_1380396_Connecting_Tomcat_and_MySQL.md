---
title: "Connecting Tomcat and MySQL"
date: 2010-01-13
forum: Server Platforms
---

### Post by CyDharttha on 2010-01-13
I had a difficult time finding this, and thought it worth sharing. Probably not the proper way, but for the time being I am up and running.

Symptom:

webapp/servlet deployed to Tomcat, utilizes JDBC driver for MySQL connectivity. Upon launching application in browser and performing action requiring database interaction, exception thrown, server log:

```

*snip*
java.security.AccessControlException: access denied (java.net.SocketPermission 127.0.0.1:3306 connect,resolve)
*snip*

```

Resolution:

Add this to /etc/tomcat6/policy.d/03catalina.policy:

```

grant {
        permission java.net.SocketPermission "localhost:3306", "connect, resolve";
};

```

Reference:

[http://stackoverflow.com/questions/1357094/access-denied-when-trying-to-connect-to-mysql-using-tomcat-datasource](http://stackoverflow.com/questions/1357094/access-denied-when-trying-to-connect-to-mysql-using-tomcat-datasource)

Comments/criticism welcome!

---

### Post by srijith_bhandary on 2011-02-15
Hi
I am new to connecting tomcat to sql 

I have installed mysql and tomcat in ubuntu and both are working great!! with Java 1.6

But I don't have any idea where to start with to connect mysql with tomcat. 

I read several links.. but nothing worked for me. 

Can you please post the steps how can I connect tomcat to mysql . 

Thanks a lot!

---

