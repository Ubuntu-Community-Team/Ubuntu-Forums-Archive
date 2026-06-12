---
title: "Apache Tomcat Won't Start Mifos"
date: 2009-06-25
forum: Server Platforms
---

### Post by guywithcable on 2009-06-25
Hi all,

I'm running Ubuntu 9.04, and I've installed Apache Tomcat from the repository. When I try to run [Mifos]("http://www.mifos.org/"), it fails and puts this in the logs:

localhost.2009-06-25.log
```
INFO: HTMLManager: start: Starting web application at '/mifos'
Jun 25, 2009 11:33:43 AM org.apache.catalina.core.StandardContext listenerStart
SEVERE: Exception sending context initialized event to listener instance of class org.mifos.framework.ApplicationInitializer
java.lang.Error: java.security.AccessControlException: access denied (java.lang.RuntimePermission getClassLoader)
    at org.mifos.framework.ApplicationInitializer.init(ApplicationInitializer.java:229)
    at org.mifos.framework.ApplicationInitializer.contextInitialized(ApplicationInitializer.java:139)
    at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:3843)
    at org.apache.catalina.core.StandardContext.start(StandardContext.java:4338)
    at org.apache.catalina.manager.ManagerServlet.start(ManagerServlet.java:1247)
    at org.apache.catalina.manager.HTMLManagerServlet.start(HTMLManagerServlet.java:604)
    at org.apache.catalina.manager.HTMLManagerServlet.doGet(HTMLManagerServlet.java:129)
    at javax.servlet.http.HttpServlet.service(HttpServlet.java:617)
    at javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244)
    at java.security.AccessController.doPrivileged(Native Method)
    at javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
    at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:276)
    at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)
    at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:283)
    at org.apache.catalina.core.ApplicationFilterChain.access$000(ApplicationFilterChain.java:56)
    at org.apache.catalina.core.ApplicationFilterChain$1.run(ApplicationFilterChain.java:189)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:185)
    at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:233)
    at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:191)
    at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:525)
    at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:128)
    at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
    at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109)
    at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
    at org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:845)
    at org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
    at org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
    at java.lang.Thread.run(Thread.java:619)
Caused by: java.security.AccessControlException: access denied (java.lang.RuntimePermission getClassLoader)
    at java.security.AccessControlContext.checkPermission(AccessControlContext.java:323)
    at java.security.AccessController.checkPermission(AccessController.java:546)
    at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
    at java.lang.ClassLoader.getParent(ClassLoader.java:1233)
    at org.mifos.framework.util.helpers.ResourceLoader.getURI(ResourceLoader.java:60)
    at org.mifos.framework.components.logger.MifosLogManager.readConfiguration(MifosLogManager.java:178)
    at org.mifos.framework.components.logger.MifosLogManager.configure(MifosLogManager.java:65)
    at org.mifos.framework.ApplicationInitializer.initializeLogger(ApplicationInitializer.java:370)
    at org.mifos.framework.ApplicationInitializer.init(ApplicationInitializer.java:145)
    ... 33 more
Jun 25, 2009 11:33:45 AM org.apache.catalina.core.ApplicationContext log
```catalina.2009-06-25.log
```
Jun 25, 2009 11:33:44 AM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
Jun 25, 2009 11:33:44 AM org.apache.catalina.core.StandardContext start
SEVERE: Context [/mifos] startup failed due to previous errors
```I'm assuming it has something to do with Debian's Java security. A few articled at Mifos.org say to not use Debian's Tomcat package, but that is not an option.

Any help is greatly appreciated. :)

---

### Post by guywithcable on 2009-06-25
Any suggestions? Do Ubuntonians not use Tomcat?

---

### Post by guywithcable on 2009-06-25
I got it working!

In case anyone else wants to run Mifos on Ubuntu...

Install everything you need as told [here]("http://www.mifos.org/developers/wiki/MifosUbuntuInstall#install-prerequisites"), then run this:
```
gksu gedit /var/lib/tomcat6/conf/policy.d/05mifos.policy
```Now paste this in:
```
// These permissions are needed to get Mifos working. I could probably give
// it fewer permissions, but this will encompass eveything it needs to do.
grant {
    permission java.io.FilePermission "/var/lib/tomcat6/webapps/mifos/-", "read,write,delete";
    permission java.security.AllPermission "/var/lib/tomcat6/webapps/mifos/-";

};
```Then save and exit. Now run:
```
gksu gedit /etc/mysql/conf.d/mifos.cnf
```paste:
```
[mysqld]
# due to issue 1513
lower_case_table_names = 1
# optional, but saves disk space
innodb_file_per_table
```Save, exit. Then install/deploy Mifos using the Tomcat Admin app.

If you need to customize database settings, run
```
gksu gedit /usr/share/tomcat6/lib/deploymifosDB.properties
```and paste something like this:
```
hibernate.connection.driver_class=com.mysql.jdbc.Driver 
hibernate.connection.url=jdbc:mysql://localhost:3306/mifos 
hibernate.connection.username=mifos
hibernate.connection.password=mifos 
hibernate.dialect=org.hibernate.dialect.MySQLDialect 
hibernate.show_sql=false 
hibernate.transaction.factory_class=org.hibernate.transaction.JDBCTransactionFactory 
hibernate.cache.provider_class=org.hibernate.cache.HashtableCacheProvider 
hibernate.connection.isolation=2 
 
hibernate.c3p0.acquire_increment=1  
hibernate.c3p0.idle_test_period=100  
hibernate.c3p0.max_size=20 
hibernate.c3p0.max_statements=0  
hibernate.c3p0.min_size=5  
hibernate.c3p0.timeout=100 
```Save, exit, restart tomcat:
```
sudo /etc/init.d/tomcat6 restart
```I had trouble with the database at first, but luckily I had another installation that I exported from then imported into the new setup.

---

### Post by meonkeys on 2009-08-27
Thanks, guywithcable! This is the same thing you mentioned on the Mifos IRC channel, yes?

I added a link to this thread here: [http://www.mifos.org/developers/wiki/TomcatSecurity](http://www.mifos.org/developers/wiki/TomcatSecurity)

---

### Post by guywithcable on 2009-08-27
> **meonkeys said:**
> Thanks, guywithcable! This is the same thing you mentioned on the Mifos IRC channel, yes?

I added a link to this thread here: [http://www.mifos.org/developers/wiki/TomcatSecurity](http://www.mifos.org/developers/wiki/TomcatSecurity)

Yeah. We've been running like a charm. It works a lot better on Ubuntu than it did on Windows Server. ;)

---

