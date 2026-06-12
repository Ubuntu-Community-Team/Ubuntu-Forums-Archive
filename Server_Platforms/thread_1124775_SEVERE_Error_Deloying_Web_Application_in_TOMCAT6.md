---
title: "SEVERE Error Deloying Web Application in TOMCAT6"
date: 2009-04-13
forum: Server Platforms
---

### Post by aks1234 on 2009-04-13
I am having trouble running a webapps that i had someone wrote. I am unable to resolve. I installed java-6-sun-1.6.0.10 and it is present in /usr/lib/jvm 
I also edited /etc/default/tomcat6 and uncommented JAVA_HOME=/usr/lib/jvm/java-6-sun

Still i am getting this error. The LOG is below.

by the way this webapp runs fine on windows version of TOMCAT, in fact it runs in JBOSS, but i am unable to run it on ubuntu TOMCAT6. I removed the servlet api file from the WAR file. i read somewhere that it conflicts with tomcat.

```
Apr 13, 2009 6:18:31 PM org.apache.catalina.core.AprLifecycleListener init
INFO: The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/java/packages/lib/i386:/lib:/usr/lib
Apr 13, 2009 6:18:32 PM org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
Apr 13, 2009 6:18:32 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 2306 ms
Apr 13, 2009 6:18:32 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Apr 13, 2009 6:18:32 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.18
Apr 13, 2009 6:18:34 PM org.apache.catalina.startup.HostConfig deployWAR
INFO: Deploying web application archive admincsv.war
Apr 13, 2009 6:18:38 PM org.apache.catalina.startup.HostConfig deployWAR
[COLOR="Red"]**SEVERE: Error deploying web application archive admincsv.war**[/COLOR]
java.lang.NoClassDefFoundError: org/springframework/core/NestedExceptionUtils
	at org.springframework.core.NestedRuntimeException.getMessage(NestedRuntimeException.java:67)
	at java.lang.Throwable.getLocalizedMessage(Throwable.java:267)
	at java.lang.Throwable.toString(Throwable.java:343)
	at org.springframework.beans.factory.BeanCreationException.toString(BeanCreationException.java:150)
	at java.lang.String.valueOf(String.java:2827)
	at java.io.PrintWriter.println(PrintWriter.java:710)
	at java.lang.Throwable.printStackTrace(Throwable.java:509)
	at org.springframework.beans.factory.BeanCreationException.printStackTrace(BeanCreationException.java:176)
	at java.util.logging.SimpleFormatter.format(SimpleFormatter.java:72)
	at org.apache.juli.FileHandler.publish(FileHandler.java:129)
	at java.util.logging.Logger.log(Logger.java:472)
	at java.util.logging.Logger.doLog(Logger.java:494)
	at java.util.logging.Logger.logp(Logger.java:694)
	at org.apache.juli.logging.DirectJDKLog.log(DirectJDKLog.java:167)
	at org.apache.juli.logging.DirectJDKLog.error(DirectJDKLog.java:135)
	at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:3847)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4342)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.access$000(ContainerBase.java:123)
	at org.apache.catalina.core.ContainerBase$PrivilegedAddChild.run(ContainerBase.java:145)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:769)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:525)
	at org.apache.catalina.startup.HostConfig.deployWAR(HostConfig.java:830)
	at org.apache.catalina.startup.HostConfig.deployWARs(HostConfig.java:719)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:490)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1149)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:311)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:117)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:719)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443)
	at org.apache.catalina.core.StandardService.start(StandardService.java:516)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:578)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177)
Caused by: java.lang.ClassNotFoundException: org.springframework.core.NestedExceptionUtils
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1387)
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1233)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	... 46 more
Apr 13, 2009 6:18:39 PM org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
Apr 13, 2009 6:18:39 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
Apr 13, 2009 6:18:39 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/47  config=null
Apr 13, 2009 6:18:39 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 7072 ms
```

---

