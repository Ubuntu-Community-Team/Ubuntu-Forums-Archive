---
title: "Tomcat win't start after install"
date: 2012-07-23
forum: Server Platforms
---

### Post by flycast on 2012-07-23
Tomcat 6.0.35
Ubuntu 12.04

I am attempting to start using:
> sudo /opt/apache-tomcat-6.0.35/bin/startup.sh startAll I get is:
> Using CATALINA_BASE:   /opt/apache-tomcat-6.0.35
Using CATALINA_HOME:   /opt/apache-tomcat-6.0.35
Using CATALINA_TMPDIR: /opt/apache-tomcat-6.0.35/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/apache-tomcat-6.0.35/bin/bootstrap.jar
Usage: catalina.sh ( commands ... )
commands:
  debug             Start Catalina in a debugger
  debug -security   Debug Catalina with a security manager
  jpda start        Start Catalina under JPDA debugger
  run               Start Catalina in the current window
  run -security     Start in the current window with security manager
  start             Start Catalina in a separate window
  start -security   Start in a separate window with security manager
  stop              Stop Catalina, waiting up to 5 seconds for the process to end
  stop n            Stop Catalina, waiting up to n seconds for the process to end
  stop -force       Stop Catalina, wait up to 5 seconds and then use kill -KILL if still running
  stop n -force     Stop Catalina, wait up to n seconds and then use kill -KILL if still running
  version           What version of tomcat are you running?
Note: Waiting for the process to end and use of the -force option require that $CATALINA_PID is definedwhich looking at catalina.sh looks like the default "how to use this command" when the "start" is not included on the end?
Checking which java logged in as me (or as sudo) I get:

> eric@sl24:~$ which java
/usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java
eric@sl24:~$ sudo which java
/usr/bin/java

The shortcut /usr/bin/java points to /etc/alternatives/java which points to /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java

This is kicking my tail...any ideas anyone?

---

### Post by flycast on 2012-07-24
Found it. What a difference a fresh start the next day makes.

In catalina.sh there is a place where it runs a file to set custom environment variables if needed:
```
# Ensure that any user defined CLASSPATH variables are not used on startup,
# but allow them to be specified in setenv.sh, in rare case when it is needed.
CLASSPATH=

if [ -r "$CATALINA_BASE/bin/setenv.sh" ]; then
  . "$CATALINA_BASE/bin/setenv.sh"
elif [ -r "$CATALINA_HOME/bin/setenv.sh" ]; then
  . "$CATALINA_HOME/bin/setenv.sh"
fi
```

in my setenv.sh file I had the following line:
```
set CMIS_CONFIG="-Dexo.data.dir=$CATALINA_HOME/external/xcmis/ext-exo-data -Dorg.exoplatform.container.standalone.config=$CATALINA_HOME/external/xcmis/ext-exo-conf/exo-configuration-mysql.xml"

```For some reason when that line executed it wiped out the parameter passed to catalina.sh. That made catalina.sh use it's default behavior and echo usage instructions. I removed the "set" from the line and all is now groovy!

---

