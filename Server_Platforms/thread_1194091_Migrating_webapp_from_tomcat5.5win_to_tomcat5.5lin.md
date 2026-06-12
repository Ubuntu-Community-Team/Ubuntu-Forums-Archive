---
title: "Migrating webapp from tomcat5.5/win to tomcat5.5/linux"
date: 2009-06-22
forum: Server Platforms
---

### Post by waga on 2009-06-22
Hi all,

I am trying to transfer a site on a tomcat5.5/windows config to tomcat5.5/linux system.

So far I have a brickwall, and am struggling to get it to work properly.

I am basically getting two errors:


```
Jun 22 13:24:13 devmobile jsvc.exec[5638]: java.security.policy: error adding Entry: ^Ijava.net.MalformedURLException: no !/ in spec
Jun 22 13:24:13 devmobile last message repeated 7 times
Jun 22 13:24:14 devmobile jsvc.exec[5638]: 22-Jun-2009 13:24:14 org.apache.catalina.core.StandardContext listenerStart SEVERE: Error configuring applic
ation listener of class com.mspace.struts.listeners.MSpaceInitialisation java.lang.NoClassDefFoundError: Could not initialize class org.apache.log4j.Lo
gManager ^Iat org.apache.log4j.Logger.getLogger(Logger.java:117) ^Iat com.mspace.struts.listeners.MSpaceInitialisation.<clinit>(MSpaceInitialisation.ja
va:38) ^Iat sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method) ^Iat sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeCons
tructorAccessorImpl.java:39) ^Iat sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27) ^Iat java.lang.r
eflect.Constructor.newInstance(Constructor.java:513) ^Iat java.lang.Class.newInstance0(Class.java:355) ^Iat java.lang.Class.newInstance(Class.java:308)
 ^Iat org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:3713) ^Iat org.apache.catalina.core.Standar
```Am not bothered too much about the first error, but the second stating:
```
 org.apache.catalina.core.StandardContext listenerStart SEVERE: Error configuring applic
ation listener of class com.mspace.struts.listeners.MSpaceInitialisation java.lang.NoClassDefFoundError: Could not initialize class org.apache.log4j.Lo
gManager ^Iat org.apache.log4j.Logger.getLogger(Logger.java:117) 

```is more worrying.
I have set the CLASSPATH, JAVA_HOME and BASE_DIR env variables, and everything else works, except for this.

Any ideas anyone?

---

