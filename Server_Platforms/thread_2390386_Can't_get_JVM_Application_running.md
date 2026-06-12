---
title: "Can't get JVM Application running"
date: 2018-04-28
forum: Server Platforms
---

### Post by moritzbu on 2018-04-28
Hey guys!
Im currently working on getting a server application running and i dont quite make progress alone anymore.

Ive got myself a ubuntu 16.04 server running, which tought me a lot about the basics of Linux and a tiny bit of networking.
But now I came across an issue that i can't figure out...and i hope you experts can help me. :KS

So the plan is to start a Java VM Server application with:

```
java -jar sshresourcemanager.jar
```

I tried accessing the webinterface and it seems some parts of it are accessible, and some give me something like "HTTP ERROR 404" and a status Report saying "_The requested resource is not available._"

So i looked at the terminal output:

```
/opt/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager                                                                                                             /
Identified java executable to be: /usr/lib/jvm/java-8-oracle/jre/bin/java
Running: /usr/lib/jvm/java-8-oracle/jre/bin/java -jar /opt/caesessshresourcemana                                                                                                             ger/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager//server/sshresourcemanage                                                                                                             rserver.jar
/opt/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager                                                                                                             /
SshRM Bootstrap: 1.0.1
Apr 28, 2018 4:09:18 PM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: No server port given, using default port: 8080
Apr 28, 2018 4:09:18 PM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: To start on a different port use: java -jar sshresourcemanager[vers                                                                                                             ion].jar [options] [port]
Apr 28, 2018 4:09:18 PM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: For more information use: java -jar sshresourcemanager[version].jar                                                                                                              -h
Apr 28, 2018 4:09:18 PM org.apache.coyote.AbstractProtocol init
INFORMATION: Initializing ProtocolHandler ["http-bio-8080"]
Apr 28, 2018 4:09:18 PM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: Server administration is located at http://localhost:8080/manager
Apr 28, 2018 4:09:18 PM org.apache.catalina.core.StandardContext setPath
WARNUNG: A context path must either be an empty string or start with a '/' and d                                                                                                             o not end with a '/'. The path [/] does not meet these criteria and has been cha                                                                                                             nged to []
Apr 28, 2018 4:09:18 PM org.apache.catalina.core.StandardService startInternal
INFORMATION: Starting service Tomcat
Apr 28, 2018 4:09:18 PM org.apache.catalina.core.StandardEngine startInternal
INFORMATION: Starting Servlet Engine: Apache Tomcat/7.0.59
Apr 28, 2018 4:09:18 PM org.apache.catalina.startup.ContextConfig getDefaultWebX                                                                                                             mlFragment
INFORMATION: No global web.xml found
2018-04-28 16:09:19,527 INFO [localhost-startStop-1] FSshResourceManagerState: I                                                                                                             nitializing SshResourceManager
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Set                                                                                                             ting up logging...
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Con                                                                                                             sole logging enabled: true
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Log                                                                                                             ging level is: debug
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Con                                                                                                             sole logging level is: debug
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Max                                                                                                             imum logfile size is: 100KB
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Max                                                                                                             imum logfile backups: 10
2018-04-28 16:09:19,534 INFO [localhost-startStop-1] FSshRMStateInitializer: Sto                                                                                                             ring temporary data in: jobs
2018-04-28 16:09:19,535 INFO [localhost-startStop-1] FSshRMStateInitializer: Tem                                                                                                             porary job data will be stored at: /opt/caesessshresourcemanager/CAESES_4.3.1_Li                                                                                                             nux.x86_64/tools/sshResourceManager/jobs
2018-04-28 16:09:19,535 INFO [localhost-startStop-1] FSshRMStateInitializer: Tem                                                                                                             porary files will be deleted from the remote hosts after they have been copied b                                                                                                             ack to the ResourceManager
2018-04-28 16:09:19,535 INFO [localhost-startStop-1] FSshRMStateInitializer: Usi                                                                                                             ng JDBC driver com.mysql.jdbc.Driver
2018-04-28 16:09:19,535 INFO [localhost-startStop-1] FSshRMStateInitializer: Usi                                                                                                             ng database dialect org.hibernate.dialect.MySQLDialect
2018-04-28 16:09:19,535 INFO [localhost-startStop-1] FSshRMStateInitializer: Usi                                                                                                             ng database at jdbc:mysql://localhost/fsshrm_reconnect
2018-04-28 16:09:19,536 INFO [localhost-startStop-1] FSshRMStateInitializer: Dat                                                                                                             abase username set
2018-04-28 16:09:19,536 INFO [localhost-startStop-1] FSshRMStateInitializer: Dat                                                                                                             abase password set
2018-04-28 16:09:19,536 INFO [localhost-startStop-1] FSshRMStateInitializer: Set                                                                                                              idle connection timeout to 1800
org.hibernate.HibernateException: JDBC Driver class not found: com.mysql.jdbc.Dr                                                                                                             iver
        at org.hibernate.connection.C3P0ConnectionProvider.configure(C3P0Connect                                                                                                             ionProvider.java:123)
        at org.hibernate.connection.ConnectionProviderFactory.newConnectionProvi                                                                                                             der(ConnectionProviderFactory.java:137)
        at org.hibernate.connection.ConnectionProviderFactory.newConnectionProvi                                                                                                             der(ConnectionProviderFactory.java:79)
        at org.hibernate.cfg.SettingsFactory.createConnectionProvider(SettingsFa                                                                                                             ctory.java:425)
        at org.hibernate.cfg.SettingsFactory.buildSettings(SettingsFactory.java:                                                                                                             89)
        at org.hibernate.cfg.Configuration.buildSettingsInternal(Configuration.j                                                                                                             ava:2119)
        at org.hibernate.cfg.Configuration.buildSettings(Configuration.java:2115                                                                                                             )
        at org.hibernate.cfg.Configuration.buildSessionFactory(Configuration.jav                                                                                                             a:1339)
        at com.friendshipsystems.fsshresourcemanager.FHibernateUtil.buildSession                                                                                                             Factory(FHibernateUtil.java:169)
        at com.friendshipsystems.fsshresourcemanager.FHibernateUtil.buildSession                                                                                                             Factory(FHibernateUtil.java:138)
        at com.friendshipsystems.fsshresourcemanager.FHibernateUtil.initialize(F                                                                                                             HibernateUtil.java:79)
        at com.friendshipsystems.fsshresourcemanager.FSshRMStateInitializer.init                                                                                                             DatabaseConfig(FSshRMStateInitializer.java:1019)
        at com.friendshipsystems.fsshresourcemanager.FSshRMStateInitializer.getC                                                                                                             onfiguration(FSshRMStateInitializer.java:73)
        at com.friendshipsystems.fsshresourcemanager.FSshResourceManagerState.<i                                                                                                             nit>(FSshResourceManagerState.java:172)
        at com.friendshipsystems.fsshresourcemanager.FSshResourceManagerServlet.                                                                                                             <init>(FSshResourceManagerServlet.java:142)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstruct                                                                                                             orAccessorImpl.java:62)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingC                                                                                                             onstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
        at java.lang.Class.newInstance(Class.java:442)
        at org.apache.catalina.core.DefaultInstanceManager.newInstance(DefaultIn                                                                                                             stanceManager.java:116)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.                                                                                                             java:1148)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:10                                                                                                             87)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex                                                                                                             t.java:5262)
        at org.apache.catalina.core.StandardContext.startInternal(StandardContex                                                                                                             t.java:5550)
        at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:150)
        at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.                                                                                                             java:1575)
        at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.                                                                                                             java:1565)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.                                                                                                             java:1149)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor                                                                                                             .java:624)
        at java.lang.Thread.run(Thread.java:748)
Caused by: java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoa                                                                                                             der.java:1720)
        at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoa                                                                                                             der.java:1571)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:264)
        at org.hibernate.util.ReflectHelper.classForName(ReflectHelper.java:192)
        at org.hibernate.connection.C3P0ConnectionProvider.configure(C3P0Connect                                                                                                             ionProvider.java:118)
        ... 31 more
2018-04-28 16:09:19,655 ERROR [localhost-startStop-1] FSshResourceManagerServlet                                                                                                             : A fatal error occured
Apr 28, 2018 4:09:19 PM org.apache.catalina.core.ApplicationContext log
INFORMATION: Marking servlet SshResourceManager as unavailable
Apr 28, 2018 4:09:19 PM org.apache.catalina.core.StandardContext loadOnStartup
SCHWERWIEGEND: Servlet [SshResourceManager] in web application [/] threw load()                                                                                                              exception
com.friendshipsystems.fsshresourcemanager.FInitalizeException: JDBC Driver class                                                                                                              not found: com.mysql.jdbc.Driver
        at com.friendshipsystems.fsshresourcemanager.FHibernateUtil.initialize(F                                                                                                             HibernateUtil.java:82)
        at com.friendshipsystems.fsshresourcemanager.FSshRMStateInitializer.init                                                                                                             DatabaseConfig(FSshRMStateInitializer.java:1019)
        at com.friendshipsystems.fsshresourcemanager.FSshRMStateInitializer.getC                                                                                                             onfiguration(FSshRMStateInitializer.java:73)
        at com.friendshipsystems.fsshresourcemanager.FSshResourceManagerState.<i                                                                                                             nit>(FSshResourceManagerState.java:172)
        at com.friendshipsystems.fsshresourcemanager.FSshResourceManagerServlet.                                                                                                             <init>(FSshResourceManagerServlet.java:142)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstruct                                                                                                             orAccessorImpl.java:62)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingC                                                                                                             onstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
        at java.lang.Class.newInstance(Class.java:442)
        at org.apache.catalina.core.DefaultInstanceManager.newInstance(DefaultIn                                                                                                             stanceManager.java:116)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.                                                                                                             java:1148)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:10                                                                                                             87)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex                                                                                                             t.java:5262)
        at org.apache.catalina.core.StandardContext.startInternal(StandardContex                                                                                                             t.java:5550)
        at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:150)
        at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.                                                                                                             java:1575)
        at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.                                                                                                             java:1565)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.                                                                                                             java:1149)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor                                                                                                             .java:624)
        at java.lang.Thread.run(Thread.java:748)

Apr 28, 2018 4:09:19 PM org.apache.coyote.AbstractProtocol start
INFORMATION: Starting ProtocolHandler ["http-bio-8080"]
Apr 28, 2018 4:09:19 PM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: Server started on port 8080
Apr 28, 2018 4:09:19 PM com.friendshipsystems.FsshResourceManagerServer$3 run
INFORMATION: Started discovery service on port 49152
Apr 28, 2018 4:13:11 PM org.apache.jasper.compiler.WebXml <init>
WARNUNG: Internal Error: File /WEB-INF/web.xml not found
org.apache.xmlrpc.client.XmlRpcHttpTransportException: HTTP server returned unexpected status: Not Found
        at org.apache.xmlrpc.client.XmlRpcSunHttpTransport.getInputStream(XmlRpcSunHttpTransport.java:94)
        at org.apache.xmlrpc.client.XmlRpcStreamTransport.sendRequest(XmlRpcStreamTransport.java:152)
        at org.apache.xmlrpc.client.XmlRpcHttpTransport.sendRequest(XmlRpcHttpTransport.java:115)
        at org.apache.xmlrpc.client.XmlRpcSunHttpTransport.sendRequest(XmlRpcSunHttpTransport.java:69)
        at org.apache.xmlrpc.client.XmlRpcClientWorker.execute(XmlRpcClientWorker.java:56)
        at org.apache.xmlrpc.client.XmlRpcClient.execute(XmlRpcClient.java:167)
        at org.apache.xmlrpc.client.XmlRpcClient.execute(XmlRpcClient.java:137)
        at org.apache.xmlrpc.client.XmlRpcClient.execute(XmlRpcClient.java:126)
        at com.friendshipsystems.fsshresourcemanager.admin.FAdministrationBackend.canDoAdministration(FAdministrationBackend.java:64)
        at com.friendshipsystems.fsshresourcemanager.admin.FAdministrationBackend.writeMenu(FAdministrationBackend.java:75)
        at org.apache.jsp.index_jsp._jspService(index_jsp.java:127)
        at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:727)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:432)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:395)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:339)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:727)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:303)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:220)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:122)
        at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:613)
        at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:613)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:170)
        at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:103)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:116)
        at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:421)
        at org.apache.coyote.http11.AbstractHttp11Processor.process(AbstractHttp11Processor.java:1074)
        at org.apache.coyote.AbstractProtocol$AbstractConnectionHandler.process(AbstractProtocol.java:611)
        at org.apache.tomcat.util.net.JIoEndpoint$SocketProcessor.run(JIoEndpoint.java:314)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
        at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
        at java.lang.Thread.run(Thread.java:748)
org.apache.xmlrpc.client.XmlRpcHttpTransportException: HTTP server returned unexpected status: Not Found
        at org.apache.xmlrpc.client.XmlRpcSunHttpTransport.getInputStream(XmlRpcSunHttpTransport.java:94)
        at org.apache.xmlrpc.client.XmlRpcStreamTransport.sendRequest(XmlRpcStreamTransport.java:152)
        at org.apache.xmlrpc.client.XmlRpcHttpTransport.sendRequest(XmlRpcHttpTransport.java:115)
        at org.apache.xmlrpc.client.XmlRpcSunHttpTransport.sendRequest(XmlRpcSunHttpTransport.java:69)
        at org.apache.xmlrpc.client.XmlRpcClientWorker.execute(XmlRpcClientWorker.java:56)
        at org.apache.xmlrpc.client.XmlRpcClient.execute(XmlRpcClient.java:167)
        at org.apache.xmlrpc.client.XmlRpcClient.execute(XmlRpcClient.java:137)
        at org.apache.xmlrpc.client.XmlRpcClient.execute(XmlRpcClient.java:126)
        at com.friendshipsystems.fsshresourcemanager.admin.FAdministrationBackend.canDoAdministration(FAdministrationBackend.java:64)
        at org.apache.jsp.index_jsp._jspService(index_jsp.java:206)
        at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:727)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:432)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:395)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:339)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:727)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:303)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:220)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:122)
        at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:613)
        at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:613)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:170)
        at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:103)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:116)
        at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:421)
        at org.apache.coyote.http11.AbstractHttp11Processor.process(AbstractHttp11Processor.java:1074)
        at org.apache.coyote.AbstractProtocol$AbstractConnectionHandler.process(AbstractProtocol.java:611)
        at org.apache.tomcat.util.net.JIoEndpoint$SocketProcessor.run(JIoEndpoint.java:314)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
        at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
        at java.lang.Thread.run(Thread.java:748)


```

Unfortunately this doesn't really speak to me.
Can you help me figuring out, what went wrong?:confused:

Best Regards
Moritz

---

### Post by moritzbu on 2018-04-28
I've managed to resolve the issue with the database connection, but still the site's behavior is identical.

This is the terminal output:

```
root@manfred:/opt/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager# java -jar sshresource                                                                                                                       nager.jar
/opt/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager/
Identified java executable to be: /usr/lib/jvm/java-8-oracle/jre/bin/java
Running: /usr/lib/jvm/java-8-oracle/jre/bin/java -jar /opt/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/ss                                                                                                                       hResourceManager//server/sshresourcemanagerserver.jar
/opt/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager/
SshRM Bootstrap: 1.0.1
Apr 29, 2018 12:46:20 AM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: No server port given, using default port: 8080
Apr 29, 2018 12:46:20 AM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: To start on a different port use: java -jar sshresourcemanager[version].jar [options] [port]
Apr 29, 2018 12:46:20 AM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: For more information use: java -jar sshresourcemanager[version].jar -h
Apr 29, 2018 12:46:20 AM org.apache.coyote.AbstractProtocol init
INFORMATION: Initializing ProtocolHandler ["http-bio-8080"]
Apr 29, 2018 12:46:20 AM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: Server administration is located at http://localhost:8080/manager
Apr 29, 2018 12:46:20 AM org.apache.catalina.core.StandardContext setPath
**WARNUNG: A context path must either be an empty string or start with a '/' and do not end with a '/'. The path [/] doe                                                                                                                       s not meet these criteria and has been changed to []**
Apr 29, 2018 12:46:20 AM org.apache.catalina.core.StandardService startInternal
INFORMATION: Starting service Tomcat
Apr 29, 2018 12:46:20 AM org.apache.catalina.core.StandardEngine startInternal
INFORMATION: Starting Servlet Engine: Apache Tomcat/7.0.59
Apr 29, 2018 12:46:20 AM org.apache.catalina.startup.ContextConfig getDefaultWebXmlFragment
**INFORMATION: No global web.xml found**
2018-04-29 00:46:21,681 INFO [localhost-startStop-1] FSshResourceManagerState: Initializing SshResourceManager
2018-04-29 00:46:21,690 INFO [localhost-startStop-1] FSshRMStateInitializer: Setting up logging...
2018-04-29 00:46:21,690 INFO [localhost-startStop-1] FSshRMStateInitializer: Console logging enabled: true
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Logging level is: debug
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Console logging level is: debug
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Maximum logfile size is: 100KB
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Maximum logfile backups: 10
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Storing temporary data in: jobs
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Temporary job data will be stored at: /op                                                                                                                       t/caesessshresourcemanager/CAESES_4.3.1_Linux.x86_64/tools/sshResourceManager/jobs
2018-04-29 00:46:21,691 INFO [localhost-startStop-1] FSshRMStateInitializer: Temporary files will be deleted from the                                                                                                                        remote hosts after they have been copied back to the ResourceManager
2018-04-29 00:46:21,692 INFO [localhost-startStop-1] FSshRMStateInitializer: Using JDBC driver org.mariadb.jdbc.Driver
2018-04-29 00:46:21,692 INFO [localhost-startStop-1] FSshRMStateInitializer: Using database dialect org.hibernate.dial                                                                                                                       ect.MySQLDialect
2018-04-29 00:46:21,692 INFO [localhost-startStop-1] FSshRMStateInitializer: Using database at jdbc:mariadb://localhos                                                                                                                       t/fsshrm_reconnect
2018-04-29 00:46:21,692 INFO [localhost-startStop-1] FSshRMStateInitializer: Database username set
2018-04-29 00:46:21,692 INFO [localhost-startStop-1] FSshRMStateInitializer: Database password set
2018-04-29 00:46:21,693 INFO [localhost-startStop-1] FSshRMStateInitializer: Set idle connection timeout to 1800
2018-04-29 00:46:22,391 INFO [localhost-startStop-1] FSshRMStateInitializer: Performing RSA check
2018-04-29 00:46:22,459 INFO [localhost-startStop-1] FSshRMStateInitializer: RSA check complete.
2018-04-29 00:46:22,459 INFO [localhost-startStop-1] FSshRMStateInitializer: Using known hosts file: known_hosts
2018-04-29 00:46:22,460 INFO [localhost-startStop-1] FSshRMStateInitializer: Mailer function disabled
2018-04-29 00:46:22,461 INFO [localhost-startStop-1] FHostManager: Setting host disable strategy to ALL
2018-04-29 00:46:22,461 INFO [localhost-startStop-1] FHostManager: Disabling periodic host availability checks.
2018-04-29 00:46:22,461 INFO [localhost-startStop-1] FHostManager: Disabling notification mails for automatic host man                                                                                                                       agement.
2018-04-29 00:46:22,462 INFO [localhost-startStop-1] FHostManager: Rescheduling jobs that failed due to connection pro                                                                                                                       blems
2018-04-29 00:46:22,462 INFO [localhost-startStop-1] FSshRMStateInitializer: Setting scheduler fairness criterion to o                                                                                                                       wner.
2018-04-29 00:46:22,464 INFO [localhost-startStop-1] FSshRMStateInitializer: Using scheduler class: com.friendshipsyst                                                                                                                       ems.fsshresourcemanager.FScheduler
2018-04-29 00:46:22,464 DEBUG [localhost-startStop-1] FScheduler: Setting scheduler priority to "priority"
2018-04-29 00:46:22,466 INFO [localhost-startStop-1] FSshRMStateInitializer: X forwarding is defaulted to: localhost:6                                                                                                                       000
2018-04-29 00:46:22,466 INFO [localhost-startStop-1] FSshRMStateInitializer: Setting file transfer timeout to : 60000
2018-04-29 00:46:22,467 INFO [localhost-startStop-1] FSshRMStateInitializer: Output buffer is set to: 10MB
2018-04-29 00:46:22,468 INFO [localhost-startStop-1] FSshRMStateInitializer: Result file server started on port 41345
2018-04-29 00:46:22,469 INFO [localhost-startStop-1] FSshRMStateInitializer: Input file server started on port 33218
2018-04-29 00:46:22,469 INFO [localhost-startStop-1] FSshRMStateInitializer: Users will NOT be able to execute multipl                                                                                                                       e commands by adding them to the arguments using '&&', '||' or ';'.
2018-04-29 00:46:22,469 INFO [localhost-startStop-1] FSshRMStateInitializer: Using command line "echo HELLO" for confi                                                                                                                       guration tests on all hosts.
2018-04-29 00:46:22,471 INFO [localhost-startStop-1] FSshRMStateInitializer: **No LDAP authentication configured**
Apr 29, 2018 12:46:22 AM org.apache.catalina.core.ApplicationContext log
**INFORMATION: Marking servlet SshResourceManager as unavailable**
Apr 29, 2018 12:46:22 AM org.apache.catalina.core.StandardContext loadOnStartup
[B]SCHWERWIEGEND: Servlet [SshResourceManager] in web application [/] threw load() exception
java.sql.SQLException: Table 'fsshrm_reconnect.FSSHRM_OPERATING_SYSTEMS' doesn't exist[/B]
Query is: select foperating0_.OS_ID as OS1_5_, foperating0_.name as name5_, foperating0_.parentId as parentId5_, foper                                                                                                                       ating0_.chdirCommand as chdirCom4_5_, foperating0_.pathDelimiter as pathDeli5_5_, foperating0_.cancelerClassName as ca                                                                                                                       nceler6_5_ from FSSHRM_OPERATING_SYSTEMS foperating0_ order by foperating0_.name asc
        at org.mariadb.jdbc.internal.util.LogQueryTool.exceptionWithQuery(LogQueryTool.java:153)
        at org.mariadb.jdbc.internal.protocol.AbstractQueryProtocol.executeQuery(AbstractQueryProtocol.java:254)
        at org.mariadb.jdbc.MariaDbPreparedStatementClient.executeInternal(MariaDbPreparedStatementClient.java:209)
        at org.mariadb.jdbc.MariaDbPreparedStatementClient.execute(MariaDbPreparedStatementClient.java:150)
        at org.mariadb.jdbc.MariaDbPreparedStatementClient.executeQuery(MariaDbPreparedStatementClient.java:164)
        at com.mchange.v2.c3p0.impl.NewProxyPreparedStatement.executeQuery(NewProxyPreparedStatement.java:76)
        at org.hibernate.jdbc.AbstractBatcher.getResultSet(AbstractBatcher.java:208)
        at org.hibernate.loader.Loader.getResultSet(Loader.java:1812)
        at org.hibernate.loader.Loader.doQuery(Loader.java:697)
        at org.hibernate.loader.Loader.doQueryAndInitializeNonLazyCollections(Loader.java:259)
        at org.hibernate.loader.Loader.doList(Loader.java:2232)
        at org.hibernate.loader.Loader.listIgnoreQueryCache(Loader.java:2129)
        at org.hibernate.loader.Loader.list(Loader.java:2124)
        at org.hibernate.loader.hql.QueryLoader.list(QueryLoader.java:401)
        at org.hibernate.hql.ast.QueryTranslatorImpl.list(QueryTranslatorImpl.java:363)
        at org.hibernate.engine.query.HQLQueryPlan.performList(HQLQueryPlan.java:196)
        at org.hibernate.impl.SessionImpl.list(SessionImpl.java:1149)
        at org.hibernate.impl.QueryImpl.list(QueryImpl.java:102)
        at com.friendshipsystems.fsshresourcemanager.config.FOperatingSystem.getOperatingSystems(FOperatingSystem.java                                                                                                                       :69)
        at com.friendshipsystems.fsshresourcemanager.config.FOperatingSystem.createDefaultOperatingSystems(FOperatingS                                                                                                                       ystem.java:100)
        at com.friendshipsystems.fsshresourcemanager.FSshResourceManagerState.<init>(FSshResourceManagerState.java:177                                                                                                                       )
        at com.friendshipsystems.fsshresourcemanager.FSshResourceManagerServlet.<init>(FSshResourceManagerServlet.java                                                                                                                       :142)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
        at java.lang.Class.newInstance(Class.java:442)
        at org.apache.catalina.core.DefaultInstanceManager.newInstance(DefaultInstanceManager.java:116)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.java:1148)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:1087)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContext.java:5262)
        at org.apache.catalina.core.StandardContext.startInternal(StandardContext.java:5550)
        at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:150)
        at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.java:1575)
        at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.java:1565)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
        at java.lang.Thread.run(Thread.java:748)

Apr 29, 2018 12:46:22 AM org.apache.coyote.AbstractProtocol start
INFORMATION: Starting ProtocolHandler ["http-bio-8080"]
Apr 29, 2018 12:46:22 AM com.friendshipsystems.FsshResourceManagerServer start
INFORMATION: Server started on port 8080
Apr 29, 2018 12:46:22 AM com.friendshipsystems.FsshResourceManagerServer$3 run
INFORMATION: Started discovery service on port 49152
```

I highlighted the outputs that seem to indicate something being wrong.
But what is the actual issue here? Has anyone got an idea?

Best Regards
Moritz

---

### Post by LHammonds on 2018-04-30
Have you tried for support on the [CASES forum]("https://www.caeses.com/forum/index.php?/forum/7-installation/")?

Looking at their [Download page]("https://www.caeses.com/downloads/"), the current Linux download version is [4.3.1]("https://www.caeses.com/downloads/software/software-archive/CAESES_4.3.1_Linux.x86_64.tar.bz2") which looks like the version you are running.

On the download page, they say you have to have a 3D GPU driver installed:
> Please install a proprietary 3D GPU driver on your Linux distribution  (OpenGL GLX extension required). You have to have a running DBUS message  bus.

Their install instructions for the software sound fairly simple too:
> For Linux, extract it (tar xf CAESES_4.2.X_Linux.x86_64.tar.bz2), change the working directory to the CAESES® folder and start with: ./CAESES
If you extracted the archive as root, you have to change the group permission, to the group your users are in (chgrp -R YOURGROUPNAME CAESES_4.2.X_Linux.x86_64).

There was no mention that you needed to install Oracle Java and start anything directly with Java.  It seems to be controlled via the "CAESES" executable (whether binary or script, I do not know).

I have seen this posted by a moderator on their site regarding questions about installing on Linux:

> On linux systems there is no need to install CAESES.
 You only need to extract the archive.

 Which is also stated below the download link on our website.

 "For Linux, extract CAESES.tar.gz, change the working directory to the CAESES[SUP]®[/SUP] folder and start with: ./CAESES"- [Reference Link]("https://www.caeses.com/forum/index.php?/topic/580-installation-caeses-in-ubuntu-15/") (Ubuntu 15)

> 
An installation like a windows installation is not necessary. Simply  download the tar.bz2. Extract it and run it. If it is running the first  time, you need to register your installation in case of a commercial use  or you need to create a CAESES access. Everything is managed with the  same start binary.

```

# open a Terminal
 
# goto your favorite folder
cd /opt
 
# download CAESES-FFW
wget http://www.friendship-systems.com/downloads/software/software-archive/CAESES-FFW_3.0.9_Linux.x86_64.tar.bz2
 
# extract the container
tar xf CAESES-FFW_3.0.9_Linux.x86_64.tar.bz2
 
# start the application
./CAESES-FFW_3.0.9_Linux.x86_64/CAESES-FFW.sh

```

 - [Reference Link]("https://www.caeses.com/forum/index.php?/topic/103-ubuntu-1204-installation/#entry315") (Ubuntu 12)

I hope this helps.  I have never seen this program before so I don't have any hands-on experience with it.

Good luck,
LHammonds

---

