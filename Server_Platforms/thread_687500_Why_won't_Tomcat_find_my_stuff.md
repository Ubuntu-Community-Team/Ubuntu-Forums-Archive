---
title: "Why won't Tomcat find my stuff?"
date: 2008-02-04
forum: Server Platforms
---

### Post by Kazade on 2008-02-04
OK this is a bit of a long story...

My company inherited a Tomcat/JSP site that we needed to rehost. With some fiddling I managed to get this site working on a Suse VM and it's running fine. I now need to fix in a minor bug in the site so I went to set up Tomcat etc. on Ubuntu for development...

The application we inherited looks for an XML file by looking in the folders on the classpath. On the SuseVM this XML file sits in /usr/share/tomcat5/common/classes and is found by the application... on Ubuntu with almost exactly the same set up, it can't find it. I've tried putting the XML file in the following places:

/usr/share/tomcat5/common/classes
/var/lib/tomcat5/shared/classes
$WEBAPP/WEB-INF/classes

It doesn't find it at all. I've been at this all day and I still can't figure out why this file is not being picked up. The only log output I get is:

```
Resource 'serverPlatform.xml' could not be found in the CLASSPATH (/usr/lib/jvm/java-6-sun-1.6.0.00/lib/tools.jar:/usr/share/tomcat5/bin/commons-launcher.jar
:/usr/share/tomcat5/bin/commons-logging-api.jar:/usr/share/tomcat5/bin/jmx.jar:/usr/lib/jvm/java-6-sun-1.6.0.00/jre//lib/jcert.jar:/usr/lib/jvm/java-6-sun-1.
6.0.00/jre//lib/jnet.jar:/usr/lib/jvm/java-6-sun-1.6.0.00/jre//lib/jsse.jar:/usr/share/tomcat5/bin/bootstrap.jar:/usr/share/tomcat5/bin/commons-logging-api.j
ar), nor could it be located by the classloader responsible for the web application (WEB-INF/classes): java.security.AccessControlException: access denied (j
ava.io.FilePermission /usr/share/tomcat5/bin/commons-logging-api.jar/serverPlatform.xml read)
```

Now, ignoring the access denied stuff, none of the paths that are supposed to be there are listed.

Any help would be appreciated

---

