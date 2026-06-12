---
title: "Tomcat-problems"
date: 2009-12-15
forum: Server Platforms
---

### Post by slogum on 2009-12-15
Hi there.

I'm having a problem with Tomcat and executing queries to my local mysql-server.

Here is my error-message:

> type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

javax.servlet.ServletException: Could not initialize class tools.DBConnection
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:294)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)

root cause

java.lang.NoClassDefFoundError: Could not initialize class tools.DBConnection
	tools.DBHandler.<init>(DBHandler.java:15)
	servlets.DBTest.doGet(DBTest.java:26)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:617)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	sun.reflect.GeneratedMethodAccessor35.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:597)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:276)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)

note The full stack trace of the root cause is available in the Apache Tomcat/6.0.18 logs.

As you can see there's something wrong with the privileges. 

I'm running a servlet that tries to connect to run a method that returns a String in the DBHandler wich in turns uses a DBConnection-class to get a Connection-object to the database. When I run it locally in JAva it runs fine, no problems with the connection. But it seems like I can't establish a connection when I run the "Connection con = DriverManager.getConnection(url, user, pass)". 

Really annoying problem. As I said, servlets and jsp's run fine, but servlets trying to communicate with SQL just ends up with problems.

Any suggestions? :)

---

