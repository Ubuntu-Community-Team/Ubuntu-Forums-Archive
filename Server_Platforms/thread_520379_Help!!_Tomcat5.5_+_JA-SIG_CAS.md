---
title: "Help!! Tomcat5.5 + JA-SIG CAS"
date: 2007-08-08
forum: Server Platforms
---

### Post by alvinistic on 2007-08-08
Hi everyone.

I've been trying to setup JA-SIG Central Authentication Service (CAS) in my Ubuntu Feisty machine. 

So far, I have managed to get Tomcat running and can get the welcome page when I direct firefox to
[http://localhost:8180]("http://localhost:8180")

I'm also able to get the sample.war from [http://tomcat.apache.org/tomcat-5.5-doc/appdev/sample/ ]("http://tomcat.apache.org/tomcat-5.5-doc/appdev/sample/") working by putting the sample.war into /var/lib/tomcat5.5/webapps and use firefox to open [http://localhost:8180/sample]("http://localhost:8180/sample")

But the problem is I can't get the sample file from CAS working. I copy the target/cas.war into /var/lib/tomcat5.5/webapps and use firefox to open [http://localhost:8180/cas](http://localhost:8180/cas) and it gives me:

HTTP Status 404 - /cas/
The requested resource (/cas/) is not available.

I checked the catalina.out. The result is as follows:
> 08-Aug-07 PM 04:32 org.apache.catalina.startup.HostConfig deployWAR
SEVERE: Error deploying web application archive cas.war
org.apache.commons.logging.LogConfigurationException: java.lang.ExceptionInInitializerError (Caused by java.lang.ExceptionInInitializerError)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:538)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:235)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:370)
	at org.apache.catalina.core.ContainerBase.getLogger(ContainerBase.java:380)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4114)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:759)
	at org.apache.catalina.core.ContainerBase.access$0(ContainerBase.java:743)
	at org.apache.catalina.core.ContainerBase$PrivilegedAddChild.run(ContainerBase.java:143)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:737)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:524)
	at org.apache.catalina.startup.HostConfig.deployWAR(HostConfig.java:809)
	at org.apache.catalina.startup.HostConfig.deployWARs(HostConfig.java:698)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:472)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1122)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:310)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1021)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:718)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1013)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:442)
	at org.apache.catalina.core.StandardService.start(StandardService.java:450)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:709)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:551)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:294)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177)
Caused by: java.lang.ExceptionInInitializerError
	at org.apache.log4j.Logger.getLogger(Logger.java:104)
	at org.apache.commons.logging.impl.Log4JLogger.getLogger(Log4JLogger.java:283)
	at org.apache.commons.logging.impl.Log4JLogger.<init>(Log4JLogger.java:108)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:529)
	... 33 more
Caused by: java.security.AccessControlException: access denied (java.io.FilePermission cas.log write)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:323)
	at java.security.AccessController.checkPermission(AccessController.java:546)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
	at java.lang.SecurityManager.checkWrite(SecurityManager.java:962)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:169)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at org.apache.log4j.FileAppender.setFile(FileAppender.java:289)
	at org.apache.log4j.RollingFileAppender.setFile(RollingFileAppender.java:165)
	at org.apache.log4j.FileAppender.activateOptions(FileAppender.java:163)
	at org.apache.log4j.config.PropertySetter.activate(PropertySetter.java:256)
	at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:132)
	at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:96)
	at org.apache.log4j.PropertyConfigurator.parseAppender(PropertyConfigurator.java:654)
	at org.apache.log4j.PropertyConfigurator.parseCategory(PropertyConfigurator.java:612)
	at org.apache.log4j.PropertyConfigurator.configureRootCategory(PropertyConfigurator.java:509)
	at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:415)
	at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:441)
	at org.apache.log4j.helpers.OptionConverter.selectAndConfigure(OptionConverter.java:468)
	at org.apache.log4j.LogManager.<clinit>(LogManager.java:122)
	... 41 more

Please help! Thanks in advance.

---

### Post by onehotcutey on 2008-01-09
Did you ever manage to get CAS working with Ubuntu?  I am needing to set it up in Gutsy and looking for any help?

Thanks.

---

