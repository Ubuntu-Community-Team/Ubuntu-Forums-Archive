---
title: "jsvc error"
date: 2009-08-17
forum: Server Platforms
---

### Post by kg4gyt on 2009-08-17
I'm working on running an instance of Tomcat 6 (I'm taking advantage of the Tomcat6-Users feature so the Catlina Base and Temp directories might look strange) that I'd like to run on port 80 using jsvc, but it keeps complaining and won't run properly.

I'm running a script with the following:

```

DSPACE_USER='dspace'

TOMCAT_LOG='/var/log/tomcat6'

CATALINA_BASE='/var/lib/tomcat6/dspace'
CATALINA_HOME='/usr/share/tomcat6'
CATALINA_TMPDIR='/var/lib/tomcat6/dspace/temp'

COMMONS_DAEMON='/usr/share/java/commons-daemon.jar'

PID_FILE='/var/run/jsvc.pid'

JRE_HOME='/usr/lib/jvm/java-6-sun'

JAVA_HOME=$JRE_HOME

jsvc \
        -user $DSPACE_USER \
        -home $JAVA_HOME \
        -cp $COMMONS_DAEMON:$CATALINA_HOME/bin/bootstrap.jar \
        -outfile $CATALINA_BASE/logs/catalina.out \
        -errfile $CATALINA_BASE/logs/catalina.err \
        -pidfile $PID_FILE \
        \
        -Xmx2048m \
        -XX:MaxPermSize=1024m \
        -wait 10 \
        -Djava.endorsed.dirs=$CATALINA_HOME/common/endorsed \
        -Dcatalina.base=$CATALINA_BASE \
        -Dcatalina.home=$CATALINA_HOME \
        -Djava.io.tmpdir=$CATALINA_TMPDIR \
        org.apache.catalina.startup.Bootstrap.start


```

The output to the log is always

```
java.lang.ClassNotFoundException: org.apache.catalina.startup.Bootstrap.start
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at org.apache.commons.daemon.support.DaemonLoader.load(DaemonLoader.java:107)
Cannot load daemon
Service exit with a return value of 3

```

Any thoughts at all?

---

### Post by kg4gyt on 2009-08-17
It looks like the tutorial that I followed was off a bit on the script.

It should have read:

```
DSPACE_USER='dspace'

TOMCAT_LOG='/var/log/tomcat6'

CATALINA_BASE='/var/lib/tomcat6/dspace'
CATALINA_HOME='/usr/share/tomcat6'
CATALINA_TMPDIR='/var/lib/tomcat6/dspace/temp'

COMMONS_DAEMON='/usr/share/java/commons-daemon.jar'

PID_FILE='/var/run/jsvc.pid'

JRE_HOME='/usr/lib/jvm/java-6-sun'

JAVA_HOME=$JRE_HOME

jsvc \
        -user $DSPACE_USER \
        -home $JAVA_HOME \
        -cp $COMMONS_DAEMON:$CATALINA_HOME/bin/bootstrap.jar \
        -outfile $CATALINA_BASE/logs/catalina.out \
        -errfile $CATALINA_BASE/logs/catalina.err \
        -pidfile $PID_FILE \
        \
        -Xmx2048m \
        -XX:MaxPermSize=1024m \
        -wait 10 \
        -Djava.endorsed.dirs=$CATALINA_HOME/common/endorsed \
        -Dcatalina.base=$CATALINA_BASE \
        -Dcatalina.home=$CATALINA_HOME \
        -Djava.io.tmpdir=$CATALINA_TMPDIR \
        org.apache.catalina.startup.Bootstrap
```

Notice that the last line no longer has .start at the end.

---

