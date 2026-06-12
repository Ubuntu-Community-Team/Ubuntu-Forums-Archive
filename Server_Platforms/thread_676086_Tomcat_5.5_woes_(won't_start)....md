---
title: "Tomcat 5.5 woes (won't start)..."
date: 2008-01-23
forum: Server Platforms
---

### Post by atrus123 on 2008-01-23
I've been having some issues getting Tomcat 5.5 started.

My machine is running Gutsy, and I installed Tomcat from the repositories.  Apache works fine, but when I try localhost:8180, I just get a not found error.

Running netstat -l -t | grep tomcat, I get nothing, so Tomcat isn't even listening, even though I get no errors when trying to start it.  Also, ps -A | grep tomcat gets a blank.

/etc/default/tomcat5.5 reads:

```
TOMCAT5_USER=tomcat55
JAVA_HOME=/usr/lib/jvm/java-6-sun
JDK_DIRS=/usr/lib/jvm/java-6-sun
TOMCAT5_SECURITY=no
```

/var/log/tomcat5.5/localhost.log reads:

```
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java
:293)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(Lifecycl
eSupport.java:120)
        at org.apache.catalina.core.ContainerBase.backgroundProcess(ContainerBas
e.java:1306)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1570)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1579)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.r
un(ContainerBase.java:1559)
        at java.lang.Thread.run(Thread.java:619)
Jan 22, 2008 9:51:32 AM org.apache.catalina.core.StandardContext loadOnStartup
SEVERE: Servlet /dspace-oai threw load() exception
java.security.AccessControlException: access denied (java.util.PropertyPermissio
n dspace.configuration read)
        at java.security.AccessControlContext.checkPermission(AccessControlConte
xt.java:323)
        at java.security.AccessController.checkPermission(AccessController.java:
546)
        at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
        at java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:12
85)
        at java.lang.System.getProperty(System.java:652)
        at org.dspace.core.ConfigurationManager.loadConfig(ConfigurationManager.
java:466)
        at org.dspace.app.webui.servlet.LoadDSpaceConfig.init(LoadDSpaceConfig.j
ava:61)
        at javax.servlet.GenericServlet.init(GenericServlet.java:211)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244
)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
        at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:2
76)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.
java:162)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.
java:115)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.
java:1133)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:96
6)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex
t.java:3956)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4
230)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase
.java:760)
        at org.apache.catalina.core.ContainerBase.access$0(ContainerBase.java:74
4)
        at org.apache.catalina.core.ContainerBase$PrivilegedAddChild.run(Contain
erBase.java:144)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:73
8)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:544)
        at org.apache.catalina.startup.HostConfig.deployWAR(HostConfig.java:825)
        at org.apache.catalina.startup.HostConfig.deployWARs(HostConfig.java:714
)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:490
)
        at org.apache.catalina.startup.HostConfig.check(HostConfig.java:1206)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java
:293)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(Lifecycl
eSupport.java:120)
        at org.apache.catalina.core.ContainerBase.backgroundProcess(ContainerBas
e.java:1306)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1570)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1579)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.r
un(ContainerBase.java:1559)
        at java.lang.Thread.run(Thread.java:619)
Jan 22, 2008 9:51:36 AM org.apache.catalina.core.ApplicationContext log
SEVERE: StandardWrapper.Throwable
java.security.AccessControlException: access denied (java.util.PropertyPermissio
n dspace.configuration read)
        at java.security.AccessControlContext.checkPermission(AccessControlConte
xt.java:323)
        at java.security.AccessController.checkPermission(AccessController.java:
546)
        at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
        at java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:12
85)
        at java.lang.System.getProperty(System.java:652)
        at org.dspace.core.ConfigurationManager.loadConfig(ConfigurationManager.
java:466)
        at org.dspace.app.webui.servlet.LoadDSpaceConfig.init(LoadDSpaceConfig.j
ava:61)
        at javax.servlet.GenericServlet.init(GenericServlet.java:211)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244
)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
        at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:2
76)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.
java:162)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.
java:115)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.
java:1133)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:96
6)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex
t.java:3956)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4
230)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase
.java:760)
        at org.apache.catalina.core.ContainerBase.access$0(ContainerBase.java:74
4)
        at org.apache.catalina.core.ContainerBase$PrivilegedAddChild.run(Contain
erBase.java:144)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:73
8)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:544)
        at org.apache.catalina.startup.HostConfig.deployWAR(HostConfig.java:825)
        at org.apache.catalina.startup.HostConfig.deployWARs(HostConfig.java:714
)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:490
)
        at org.apache.catalina.startup.HostConfig.check(HostConfig.java:1206)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java
:293)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(Lifecycl
eSupport.java:120)
        at org.apache.catalina.core.ContainerBase.backgroundProcess(ContainerBas
e.java:1306)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1570)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1579)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.r
un(ContainerBase.java:1559)
        at java.lang.Thread.run(Thread.java:619)
Jan 22, 2008 9:51:36 AM org.apache.catalina.core.StandardContext loadOnStartup
SEVERE: Servlet /dspace threw load() exception
java.security.AccessControlException: access denied (java.util.PropertyPermissio
n dspace.configuration read)
        at java.security.AccessControlContext.checkPermission(AccessControlConte
xt.java:323)
        at java.security.AccessController.checkPermission(AccessController.java:
546)
        at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
        at java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:12
85)
        at java.lang.System.getProperty(System.java:652)
        at org.dspace.core.ConfigurationManager.loadConfig(ConfigurationManager.
java:466)
        at org.dspace.app.webui.servlet.LoadDSpaceConfig.init(LoadDSpaceConfig.j
ava:61)
        at javax.servlet.GenericServlet.init(GenericServlet.java:211)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244
)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
        at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:2
76)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.
java:162)
        at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.
java:115)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.
java:1133)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:96
6)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex
t.java:3956)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4
230)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase
.java:760)
        at org.apache.catalina.core.ContainerBase.access$0(ContainerBase.java:74
4)
        at org.apache.catalina.core.ContainerBase$PrivilegedAddChild.run(Contain
erBase.java:144)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:73
8)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:544)
        at org.apache.catalina.startup.HostConfig.deployWAR(HostConfig.java:825)
        at org.apache.catalina.startup.HostConfig.deployWARs(HostConfig.java:714
)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:490
)
        at org.apache.catalina.startup.HostConfig.check(HostConfig.java:1206)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java
:293)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(Lifecycl
eSupport.java:120)
        at org.apache.catalina.core.ContainerBase.backgroundProcess(ContainerBas
e.java:1306)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1570)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.p
rocessChildren(ContainerBase.java:1579)
        at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.r
un(ContainerBase.java:1559)
        at java.lang.Thread.run(Thread.java:619)

```

Lastly, /etc/tomcat5.5/server.xml contains:

```
    <Connector port="8180" maxHttpHeaderSize="8192"
               maxThreads="150" minSpareThreads="25" maxSpareThreads="75"
               enableLookups="false" redirectPort="8443" acceptCount="100"
               connectionTimeout="20000" disableUploadTimeout="true"
               URIEncoding="UTF-8" />

```

Any thoughts of other things I could try to get this working?  I've tried reinstalling, changing the port, changing the jre, etc, but always with the same result.  I never had a problem with Tomcat on Dapper, but Gutsy has really been a pain.  I may just downgrade to Dapper and install Tomcat 6 from scratch, but I'd like to see if I can get this working first.

Thanks in advance.

---

### Post by atrus123 on 2008-01-25
Nevermind.  Upgrading to Hardy fixed it.  This is only on a test machine, so I'm not too concerned about other potential Hardy alpha bugs.

---

