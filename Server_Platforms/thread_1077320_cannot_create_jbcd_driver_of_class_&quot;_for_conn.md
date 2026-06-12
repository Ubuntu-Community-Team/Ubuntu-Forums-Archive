---
title: "cannot create jbcd driver of class &quot; for connect URL 'null' ERROR"
date: 2009-02-22
forum: Server Platforms
---

### Post by wlbragg on 2009-02-22
"cannot create jbcd driver of class " for connect URL 'null'" error trying to use JDBC.

I have looked EVERYWHERE and tried EVERYTHING for a solution to this problem.
I am trying to get an application that is currently working fine on a Windows platform to work in a Linux environment.

The one thing that is completely different from my setup in Windows, and also one that I have no experience with, is that the Linux-Ubuntu default install of Apache2.2 is using Virtual Hosts and Tomcat6's equivalent multiple instances.

I'm trying to run the application out of the usr/share/tomcat6/webapps/msgboard instance of Tomcat vs var/lib/tomcat6. I don't fully understand that whole side of this and whether or not it makes it different to configure. I found [http://ubuntuforums.org/showthread.php?t=1034957&highlight=apache+tomcat+jdbc](http://ubuntuforums.org/showthread.php?t=1034957&highlight=apache+tomcat+jdbc) and now have a question as to where the best place to run the app from would be usr/share/tomcat6/webapps/ or /var/lib/tomcat6/webapps and is that why the JDBC isn't working?

Also note I am calling the application from Apache Virtual Host port 80 using mod_jk. The application cannot run under native Tomcat because of the extensive use of PHP. Everything else in the application is working correctly including a DWR (Reverse Ajax) servlet.

Following is all the pertinent setup info or structure for reference and critique. Any suggestions would be greatly appreciated. My best guess is it is still a permissions problem but I am TOTALY unfamiliar with permissions. Either that or maybe the usr/share/tomcat6/webapps/ VS /var/lib/tomcat6/webapps issue is the problem? 

Apache2.2
Tomcat6
JDBC
mod_jk
Java (not sure what ver, it's the default Ubuntu install ver.)
PHP

##################################################
I tried the mysql-connector-java-5.1.6.jar in both
usr/share/tomcat6/lib
and
usr/share/tomcat6/webapps/msgboard/WEB-INF/lib
-----------------------------------
added
commons-dbcp.jar
and also 
commons-logging.jar
------------------------------------
####################################################
Application is running/deployed from 
----------------------------------
usr/share/tomcat6/webapps/msgboard
-----------------------------------
###################################################
The basic code snippet in class calling the JDBC
WEB-INF
	classes
		dbLink.class
-----------------------------------
DataSource ds = (DataSource)ctx.lookup("java:comp/env/jdbc/msgboardDB");
-----------------------------
###################################################
WEB-INF
	web.xml
-----------------------------------
<?xml version="1.0" encoding="ISO-8859-1"?>
	<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN" "http://java.sun.com/dtd/web-app_2_3.dtd">
<web-app id="msgboard">
	<display-name>Message Board</display-name>
	<resource-ref>
		<description>DB Connection</description>
		<res-ref-name>jdbc/msgboardDB</res-ref-name>
		<res-type>javax.sql.DataSource</res-type>
		<res-auth>Container</res-auth>
	</resource-ref>
</web-app>
-----------------------------------
###################################################
META-INF
	context.xml
----------------------------------
<?xml version="1.0" encoding="ISO-8859-1"?>
<Context path="/msgboard" docBase="msgboard"
        debug="5" reloadable="true" crossContext="true">

  <Resource name="jdbc/msgboardDB" 
		auth="Container" 
		type="javax.sql.DataSource"
               	maxActive="100" 
		maxIdle="30" 
		maxWait="10000"
               	username="root" 
		password="thePassword" 
		driverClassName="com.mysql.jdbc.Driver"
               	url="jdbc:mysql://localhost:3306/msgboard?autoReconnect=true"/>
</Context>
----------------------------------
I also included a symlink to this in var/lib/tomcat6/config named msgboard.xml 
per instruction at
[http://ubuntuforums.org/showthread.php?t=430133](http://ubuntuforums.org/showthread.php?t=430133)
I also tried a symlink to this at 
usr/share/tomcat6/skel/config
---------------------------------
####################################################
my.cnf
----------------------------------
[client]
port		= 3306
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
----------------------------------
###################################################
permissions set in
/etc/tomcat6/policy.d/04webapps.policy
---------------------------------------
permission java.net.SocketPermission "127.0.0.1:3306", "connect,resolve,listen,accept";
per instruction at
[http://ubuntuforums.org/showthread.php?t=430133](http://ubuntuforums.org/showthread.php?t=430133)
---------------------------------------
other permissions set by me trying to figure this out
/etc/tomcat6/policy.d/50local.policy
---------------------------------------
grant codeBase "file:/usr/share/tomcat6/webapps/msgboard/-" {
      	permission java.net.SocketPermission "127.0.0.1:3306", "connect,resolve,listen,accept";
};
grant codeBase "file:/usr/share/tomcat6/webapps/msgboard/WEB-INF/classes/-" {
	permission java.io.FilePermission "/usr/share/tomcat6/webapps/msgboard/WEB-INF/classes/logging.properties", "read";
};
grant codeBase "jar:file:/usr/share/tomcat6/webapps/msgboard/WEB-INF/lib/mysql-connector-java-5.1.6.jar!/-" {
      permission java.net.SocketPermission "127.0.0.1:3306", "connect,resolve,listen,accept";
};
----------------------------------------
I noticed the examples I was following used 
${CATALINA_BASE}/webapps/...... 
for the codeBase path but the application is in the equivalent of
${CATALINA_HOME}/webapps/......
I ended up using the full path
/usr/share/tomcat6/.....
instead of the environmental vars which I figured was the equivalent of
${CATALINA_HOME}/webapps/......
###################################################
I even tried setting Tomcat Security to no
per instruction at
[http://webui.sourcelabs.com/ubuntu/mail/user/threads/Tomcat_connecting_to_MySQL_-_Ubuntu_8.10_Server.meta](http://webui.sourcelabs.com/ubuntu/mail/user/threads/Tomcat_connecting_to_MySQL_-_Ubuntu_8.10_Server.meta)


What now?

---

### Post by koenn on 2009-02-23
for what it's worth :
it's probably a JDBC configuration issue.
JDBC is probably looking for these values:
```
driverClassName="com.mysql.jdbc.Driver"
url="jdbc:mysql://localhost:3306/msgboard?autoReconnect=true"/>
```
but apparently doesn't see them - it complains that Driver Class and url are empty/null string.

I know nothing about Java web apps or tomcat, so I can't tell you what to do next.

I googled tomcat configure jdbc datasource , and it returns quite a bit of info.
e.g. this one : [http://linux-bsd-central.com/index.php/content/view/93/29/](http://linux-bsd-central.com/index.php/content/view/93/29/)
note that the xml syntax is different from what you use, maybe that's wort a closer look ?

---

### Post by wlbragg on 2009-02-23
Thanks for the feedback. The different syntax I use is just a cleaner way of doing it. It shouldn't have any affect.

To farther clarify what I have tried I setup a very small test webapp (without php)to use for debugging this problem I tried calling it from native tomcat and still no luck. 

I tried to use both

```
jdbc:mysql://localhost:3306/msgboard?autoreconnect=true&user=root&password=password

and

jdbc:mysql://localhost/msgboard?autoreconnect=true&user=root&password=password

```

and got

```
bash: jdbc:mysql://localhost/msgboard?autoreconnect=true: No such file or directory
[1]7074
[2] 7048
[1]  Exit 127 jdbc:mysql://localhost/msgboard?autoreconnect=true
[2]+ Done

```

I also get this error from syslog on boot

```
Feb 23, 2009 3:01:51 PM org.directwebremoting.util.CommonsLoggingOutput info INFO: Exec: Online.getPosts() 
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: org.apache.tomcat.dbcp.dbcp.SQLNestedException: Cannot create JDBC driver of class '' for connect URL 'null'
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.tomcat.dbcp.dbcp.BasicDataSource.createDataSource(BasicDataSource.java:780)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.tomcat.dbcp.dbcp.BasicDataSource.getConnection(BasicDataSource.java:540)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat dat.DBLink.posts(DBLink.java:1600)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat Online.getPosts(Online.java:26)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat java.lang.reflect.Method.invoke(Method.java:616)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.impl.ExecuteAjaxFilter.doFilter(ExecuteAjaxFilter.java:34)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.impl.DefaultRemoter$1.doFilter(DefaultRemoter.java:428)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.impl.DefaultRemoter.execute(DefaultRemoter.java:431)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.impl.DefaultRemoter.execute(DefaultRemoter.java:283)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.servlet.PlainCallHandler.handle(PlainCallHandler.java:52)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.servlet.UrlProcessor.handle(UrlProcessor.java:101)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.directwebremoting.servlet.DwrServlet.doPost(DwrServlet.java:146)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat javax.servlet.http.HttpServlet.service(HttpServlet.java:637)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat java.lang.reflect.Method.invoke(Method.java:616)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat java.security.AccessController.doPrivileged(Native Method)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat javax.security.auth.Subject.doAsPrivileged(Subject.java:537)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:276)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:283)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.ApplicationFilterChain.access$000(ApplicationFilterChain.java:56)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.ApplicationFilterChain$1.run(ApplicationFilterChain.java:189)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat java.security.AccessController.doPrivileged(Native Method)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:185)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:233)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:191)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:128)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:845)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat java.lang.Thread.run(Thread.java:636)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: Caused by: java.sql.SQLException: No suitable driver
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat java.sql.DriverManager.getDriver(DriverManager.java:279)
Feb 23 15:01:51 ubuntu jsvc.exec[6779]: ^Iat org.apache.tomcat.dbcp.dbcp.BasicDataSource.createDataSource(BasicDataSource.java:773)
```

and one other thing I checked to make sure it was correct was the CLASSPATH which was

```
/usr/lib/jvm/java-6-sun/bin:/usr/share/tomcat6/lib/servlet-api.jar:/usr/share/tomcat6/lib/mysql-connector-java.jar
```

---

### Post by koenn on 2009-02-23
yet your still getting the same error:
org.apache.tomcat.dbcp.dbcp.SQLNestedException: Cannot create JDBC driver of class '' for connect URL 'null'

I remember seeing something similar when I was trying to let OpenOffice Base talk to a mysql back-end over jdbc, and the problem was an incorrect classpath so the driver wasn't found.
pointing to /usr/share/java/mysql-connector-java.jar worked for me.

I also have some doubts about the url you're using (although it shouldn't matter, because the error says jdbc sees nothing but a null string anyway). URL in this context is the 'resource locator' for your database, so it should look something like 
jdbc:mysql://host_name:port/database_name.

the way you pass params in the url makes me think you might be using http urls pointing to (an application on) a web server.

But like I said, I'm not a programmer, so I could be way off.

---

### Post by wlbragg on 2009-02-26
I finally figured this out.

SOLUTION

I had to add

<Resource name="jdbc/webappDB" 
	auth="Container" 
	type="javax.sql.DataSource"
 
        maxActive="100" 
	maxIdle="30" 
	maxWait="10000"
 
        username="root" 
	password="password" 
	driverClassName="com.mysql.jdbc.Driver"
 
        url="jdbc:mysql://localhost:3306/webapp?autoReconnect=true"/>



into /var/lib/tomcat6/conf/Catalina/localhost/ webapp.xml
Note: the above context file was created automatically after deploying the webapp. I had to add the <resource> to it.
The context I created in usr/share/tomcat_home/webapp/META_INF/context.xml is still there and has the same <resource> defined in it. I did not verify whether or not it still needs to be there.

After that I had to add two policies
/var/lib/tomcat6/conf/policy.d/03catalina.policy
grant {
permission java.lang.RuntimePermission "accessClassInPackage.org.apache.tomcat.dbcp.*";
};
and 04webapps.policy
permission java.net.SocketPermission "127.0.0.1:3306", "connect,resolve,listen,accept";

That did the trick!

Other things that were done but have not been verified as to have any bearing on this issue.
I changed the active java from openjdk to java-sun
I added $tomcat_home/lib:$tomcat_home/lib/mysql-connector.jar:$tomcat_home/lib/commons-dbcp.jar to PATH
Changed CLASSPATH=usr/share/classpath:usr/share/java/commons-dbcp.jar:usr/share/java/mysql-connector.jar

---

