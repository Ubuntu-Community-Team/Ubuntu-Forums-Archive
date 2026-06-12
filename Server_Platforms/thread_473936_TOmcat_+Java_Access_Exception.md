---
title: "TOmcat +Java Access Exception"
date: 2007-06-14
forum: Server Platforms
---

### Post by dean20007 on 2007-06-14
Hi folks 

I am developing a webapp currently which (attempts to) access a remote database. In windows this works fine however when I attempt to run it locally on tomcat + Ubuntu I get the stack trace below.  from what i have read this is a security and can probably be resolved my some modification Catalina.policy. but can anyone advise exactly what change has to be made

I am running Tomcat 5. Java 1.5.0 and mysql-connector-java-5.0.6-bin.jar


java.security.AccessControlException
MESSAGE: access denied (java.net.SocketPermission <outward going host> resolve)

java.security.AccessControlException: access denied (java.net.SocketPermission <outward going host> resolve)
        at java.security.AccessControlContext.checkPermission(AccessControlContext.java:264)
        at java.security.AccessController.checkPermission(AccessController.java:427)
        at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
        at java.lang.SecurityManager.checkConnect(SecurityManager.java:1031)
        at java.net.InetAddress.getAllByName0(InetAddress.java:1117)
        at java.net.InetAddress.getAllByName0(InetAddress.java:1098)
        at java.net.InetAddress.getAllByName(InetAddress.java:1061)
        at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:163)
        at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:268)
        at com.mysql.jdbc.Connection.createNewIO(Connection.java:2745)
        at com.mysql.jdbc.Connection.<init>(Connection.java:1553)
        at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
        at java.sql.DriverManager.getConnection(DriverManager.java:525)
        at java.sql.DriverManager.getConnection(DriverManager.java:171)
        at uk.co.infopick.server.util.database.ConnectionFactory.getMySQLConnection(ConnectionFactory.java:37)
        at uk.co.infopick.server.util.database.AbstractDao.getConnection(AbstractDao.java:29)
        at uk.co.infopick.server.session.store.StoredSessionDao.loadPageSessions(StoredSessionDao.java:43)
        at uk.co.infopick.server.session.store.StoredSessionManager.loadSession(StoredSessionManager.java:32)
        at uk.co.infopick.server.handler.servlet.HTTPHandlerServlet.doGet(HTTPHandlerServlet.java:69)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:689)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
        at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.access$0(ApplicationFilterChain.java:177)
        at org.apache.catalina.core.ApplicationFilterChain$1.run(ApplicationFilterChain.java:156)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:152)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:214)
        at org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:198)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:152)
        at org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:137)
        at org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
        at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:118)
        at org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:102)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109)
        at org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:929)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:160)
        at org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:799)
        at org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.processConnection(Http11Protocol.java:705)
        at org.apache.tomcat.util.net.TcpWorkerThread.runIt(PoolTcpEndpoint.java:577)
        at org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:684)
        at java.lang.Thread.run(Thread.java:595)

---

### Post by dean20007 on 2007-06-15
anyone?

---

### Post by ianhaycox on 2007-06-15
You could try editing /etc/init.d/tomcat5   and change

# Use the Java security manager? (yes/no)
TOMCAT5_SECURITY=yes

then 

sudo /etc/init.d/tomcat5 restart


Not sure I'd recommend leaving it like that, but it might get you started.

---

