---
title: "Tomcat package broken ?"
date: 2008-11-10
forum: Server Platforms
---

### Post by Dimas on 2008-11-10
Hi,

I've installed an Ubuntu Server 8.10 with the Tomcat6 package and have some problems. I've posted this to a Tomcat mailing list and they answered this -> [http://www.mail-archive.com/users@tomcat.apache.org/msg52780.html](http://www.mail-archive.com/users@tomcat.apache.org/msg52780.html)

The problem:

When I start it this msg appears on the Catalina log:

WARNING: User database is not persistable - no write permissions on directory

Do you know why? Anyway the Tomcat starts OK, but when I deploy an application (JasperServer 3.0) it doesn't start with more permissions errors on the log:

Catalina log

Nov 7, 2008 2:48:10 PM org.apache.catalina.core.NamingContextListener addResource WARNING: Failed to register in JMX: javax.naming.NamingException: Could not create resource factory instance [Root exception is java.lang.ClassNotFoundException: org.apache.tomcat.dbcp.dbcp.BasicDataSourceFactory]

...
Nov 7, 2008 2:48:13 PM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
Nov 7, 2008 2:48:13 PM org.apache.catalina.core.StandardContext start
SEVERE: Context [/jasperserver] startup failed due to previous errors

Localhost log


SEVERE: Exception sending context initialized event to listener instance of class org.springframework.web.util.Log4jConfigListener java.security.AccessControlException: access denied (java.util.PropertyPermission jasperserver.root read)

...

SEVERE: Exception sending context initialized event to listener instance of class org.springframework.web.context.ContextLoaderListener org.springframework.beans.factory.BeanDefinitionStoreException: Error registering bean with name 'fileVirtualizerFactory' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Could not resolve placeholder 'java.io.tmpdir'

...

SEVERE: Exception sending context initialized event to listener instance of class com.tonbeller.tbutils.res.ResourcesFactoryContextListener

java.lang.ExceptionInInitializerError
...

Caused by: java.security.AccessControlException: access denied (java.util.PropertyPermission tbeller.InitialResourceProvider read)

...

SEVERE: Exception sending context initialized event to listener instance of class com.jaspersoft.jasperserver.war.util.SecurityContextHolderStrategyInitializer

java.lang.ExceptionInInitializerError
...

SEVERE: Exception sending context destroyed event to listener instance of class org.springframework.web.util.Log4jConfigListener java.security.AccessControlException: access denied (java.util.PropertyPermission * read,write)

I tried to chown all tomcat6 directory to the tomcat6 user, and make a 777 pemission folder, but no result :(

Any suggestion?

Thx!

---

### Post by qbase on 2008-11-27
<edit>
My mistake, had manually removed files for tomcat6. Problem solved when I purged the packages. apt-get remove --purge tomcat6 
</edit>


I can't even install tomcat6 on my 8.10 server :mad:

If I manually create tomcat-users.xml, it will complain about files in /var/lib/tomcat6/conf/policy.d/ instead.


markus@sun-sub:/etc$ sudo apt-get install tomcat6
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  tomcat6-docs tomcat6-admin tomcat6-examples
The following NEW packages will be installed:
  tomcat6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.0kB of archives.
After this operation, 258kB of additional disk space will be used.
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) intrepid/main tomcat6 6.0.18-0ubuntu3 [23.0kB]
Fetched 23.0kB in 0s (165kB/s)
Selecting previously deselected package tomcat6.
(Reading database ... 31402 files and directories currently installed.)
Unpacking tomcat6 (from .../tomcat6_6.0.18-0ubuntu3_all.deb) ...
Setting up tomcat6 (6.0.18-0ubuntu3) ...
chgrp: cannot access `/etc/tomcat6/tomcat-users.xml': No such file or directory
dpkg: error processing tomcat6 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sdhoigt on 2009-01-07
I'm having a pretty similar problem on the default Tomcat 6 install on Ubuntu 8.10.

On the very first load of Tomcat, I'm seeing some of the same problems you mentioned in the catalina log file (note: no webapps have even been deployed yet).

...
WARNING: User database is not persistable - no write permissions on directory
...
org.apache.catalina.core.NamingContextListener addResource
WARNING: Failed to register in JMX: javax.naming.NamingException: Could not create resource factory instance [Root exception is java.lang.ClassNotFoundException: org.apache.tomcat.dbcp.dbcp.BasicDataSourceFactory]


When I try to set-up a simple JNDI datasource in context.xml and restart Tomcat, I get the second warning (above) about a half dozen times.  


Is this even the same problem as you?  It sounds like you solved it by purging and reinstalling (since you mucked around w/some files).  This is totally a fresh install for me, so I'm at a loss.

Thanks,
sd

---

### Post by sdhoigt on 2009-01-08
I've done a little more research on this problem.  Disclaimer: I'm a Java/Tomcat newb.

This class, org.apache.tomcat.dbcp.dbcp.BasicDataSourceFactory, that is dumped to the logs as ClassNotFoundException seems to exists but under a different path.

The BasicDataSourceFactory class is within the commons-dbcp.jar of which a symlink is sitting in Tomcat's lib dir (/var/lib/tomcat6/lib).  However, digging into the jar I find the BasicDataSourceFactory class under a different package path:
org.apache.commons.dbcp.BasicDataSourceFactory.class

So (if I'm understanding this correctly) it's no wonder Tomcat complains that it cannot find this class.

Without a fix or workaround (which I wish I knew) I don't know how anyone can create any application-wide database datasources.

sd

---

### Post by sdhoigt on 2009-01-08
Here's another tidbit of info.  

Looking at the official Tomcat 6 download I see the BasicDataSourceFactory.class is in the "correct" path that Ubuntu's 8.10 Tomcat is looking for.

org.apache.tomcat.dbcp.dbcp.BasicDataSourceFactory.class  (tomcat-dbcp.jar)

So Ubuntu's 8.10 Tomcat install is effectively broken as far as I can see.  Is there a way to get Ubuntu's Tomcat to point to the non-standard location for BasicDataSourceFactory that they've settled upon?

sd

---

### Post by sdhoigt on 2009-01-10
I've filed a bug report.
[https://bugs.launchpad.net/ubuntu/+source/libcommons-dbcp-java/+bug/315314](https://bugs.launchpad.net/ubuntu/+source/libcommons-dbcp-java/+bug/315314)

In the meantime I downloaded/installed the official Tomcat 6 binary distribution.  Fortunately, all the problems I detailed above do not exist in the official build.

sd

---

