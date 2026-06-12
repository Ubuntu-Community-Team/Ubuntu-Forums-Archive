---
title: "Problem in starting up Tomcat with jsvc"
date: 2006-12-25
forum: Server Platforms
---

### Post by danielking on 2006-12-25
I can successfully startup the service with startup.sh in Tomcat's bin directory.
Now I want to make it a system service, so I try to use jsvc.

I build the jsvc binary file successfully, and try to manually run it:

```
[danielking: /data/apps/tomcat]
$ bin/jsvc-src/jsvc -user tomcat5 -cp "/data/apps/jdk1.5.0_09/lib/tools.jar:/data/apps/tomcat/bin/commons-daemon.jar:/data/apps/tomcat/bin/bootstrap.jar" -home "/data/apps/jdk1.5.0_09/" org.apache.catalina.startup.BootstrapService   
25/12/2006 13:29:40 11003 jsvc error: Cannot set group id for user 'tomcat5'
25/12/2006 13:29:40 11002 jsvc error: Error validating user 'tomcat5'
```

These IS a user named tomcat5.

And I tried to run it as a root, there was no output:
```
[danielking: /data/apps/tomcat]
$ sudo bin/jsvc-src/jsvc -user tomcat5 -cp "/data/apps/jdk1.5.0_09/lib/tools.jar:/data/apps/tomcat/bin/commons-daemon.jar:/data/apps/tomcat/bin/bootstrap.jar" -home "/data/apps/jdk1.5.0_09/" org.apache.catalina.startup.BootstrapService 
[danielking: /data/apps/tomcat]
```
But tomcat didn't stated yet.

What can i do now?

---

### Post by wangrui on 2008-01-10
I'm new to linux, but I found a solution from the web

create a script and save it to tomcat5

> #!/bin/sh
# /etc/init.d/tomcat5
#
### BEGIN INIT INFO
# Provides:             tomcat5
# Required-Start:   $network
# X-UnitedLinux-Should-Start:
# Required-Stop:   $network
# X-UnitedLinux-Should-Stop:
# Default-Start:       3 5
# Default-Stop:       0 1 2 6
# Description:         Apache-Tomcat Servlet Container
### END INIT INFO
JAVA_HOME=/usr/java/jdk1.6.0_03
CATALINA_HOME=/opt/apache-tomcat-6.0.14
DAEMON_HOME=/opt/apache-tomcat-6.0.14
TOMCAT_USER=root

TMP_DIR=/var/tmp
PID_FILE=/var/run/jsvc.pid
CATALINA_TMPDIR=/opt/apache-tomcat-6.0.14/temp
CATALINA_OPTS="-Djava.endorsed.dirs=$CATALINA_HOME/common/endorsed"
CLASSPATH=\
$JAVA_HOME/lib/tools.jar:\
$CATALINA_HOME/bin/commons-daemon.jar:\
$CATALINA_HOME/bin/bootstrap.jar
JSVC_BIN=$DAEMON_HOME/bin/jsvc

#. /etc/rc.status
#rs_reset

if [ ! -x ${JSVC_BIN} ]; then
    echo -n >$2 "Cannot run Tomcat, ${JSVC_BIN}  not present. "
    #rc_status -s
    exit 5
fi

case "$1" in
    start)
    #
    # Start Tomcat
    echo -n "Starting service Tomcat 5.0.28 Servlet Container "
    checkproc -p ${PID_FILE} ${JSVC_BIN}
   case $? in
        0) echo -n " - Warning:  daemon already running. ";;
        1) echo -n " - Warning: ${PID_FILE} exists.  ";;
    esac
    $DAEMON_HOME/bin/jsvc \
    -user $TOMCAT_USER \
    -home $JAVA_HOME \
    -Dcatalina.home=$CATALINA_HOME \
    -Dcatalina.tmpdir=$CATALINA_TMPDIR \
    -Djava.io.tmpdir=$TMP_DIR \
    -wait 10 \
    -pidfile $PID_FILE \
    -outfile $CATALINA_HOME/logs/catalina.out \
    -errfile '&1' \
    $CATALINA_OPTS \
      -Xms64M -Xmx1024M \
    -cp $CLASSPATH \
    org.apache.catalina.startup.Bootstrap \
    chown -R -H --dreference tomcat:tomcat $CATALINA_HOME/*
    #rc_status -v
    ;;
  
  stop)
    # Stop Tomcat
    echo -n "Stopping service Tomcat 5.0.28 Servlet Container "
    $DAEMON_HOME/bin/jsvc \
    -stop \
    -pidfile $PID_FILE \
    org.apache.catalina.startup.Bootstrap
    #rc_status -v
    ;;

  restart|reload|force-reload)
    $0 stop
    $0 start
    ;;

  status)
      echo -n "Checing status of Tomcat 5.0.28 Servlet Container "
      checkproc -p ${PID_FILE} ${JSVC_BIN}
      #rc_status -v
     ;;
  *)
      echo "Usage: $0 {start|stop|restart|reload|force-reload|status}"
      exit 1;;
esac
#rc_exit

and then type > ./tomcat5 start,
and make sure all files in tomcat is readable from root.
it works on my machine.

---

