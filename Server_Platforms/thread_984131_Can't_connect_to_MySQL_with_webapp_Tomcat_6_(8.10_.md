---
title: "Can't connect to MySQL with webapp Tomcat 6 (8.10 Server)"
date: 2008-11-16
forum: Server Platforms
---

### Post by akrapacs on 2008-11-16
I have a very mature web application that I have developed on my OS X machine and I have not had any problems with connecting to the MySQL database server. I recently installed 8.10 server and installed the LAMP Server and the Tomcat Servlet server. All necessary components seem to be installed and configured fine. I can log into mysql server via the command prompt and I can run access the tomcat mangager console as well as run servlets and JSPs. I've tried everything to get my servlets to connect to MySQL and I have had no success.

My original implementation, which works great in OS X:
```
Class.forName("com.mysql.jdbc.Driver");
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost/inventory?user=invuser&password=pass");
```

I have tried using localhost, 127.0.0.1, localhost:3306, 127.0.0.1:3306 and the results are the same.

And the exception:
```
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
Last packet sent to the server was 0 ms ago.
```

The most confusing part about this exception is that I receive nearly the exact same exception in OS X when I forget to start the MySql Server (i have not configure it to start automatically). However, this does not seem to be the case on my Ubuntu server because from what I can tell the MySql server is running.

After researchin online I attempte to set up a JNDI Datasource for connection pooling. I configured my context.xml file and web.xml file according to JNDI Datasource HOW-TO Tomcat6 document. Again, it works great in OS X but when I deploy the .war file to the ubuntu server i get an exception thrown.

Code to get the connection:
```
InitialContext ctx = new javax.naming.InitialContext();
DataSource ds = (DataSource)ctx.lookup("java:comp/env/jdbc/inventory");
Connection connection = ds.getConnection();
```

Exception Thrown:
```
javax.naming.NamingException: Could not create resource factory instance 
[Root exception is java.security.AccessControlException: access denied 
(java.lang.RuntimePermission accessClassInPackage.org.apache.tomcat.dbcp.dbcp)
```

Help!

---

