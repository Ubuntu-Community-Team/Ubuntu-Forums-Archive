---
title: "start-stop-daemon and java process"
date: 2009-04-01
forum: Server Platforms
---

### Post by Joel Duckworth on 2009-04-01
Hi guys I've implemented a custom java daemon using the start-stop-daemon. It works like a charm except that when it stops the process it throws a warning message like..

```
start-stop-daemon: warning: failed to kill 12172: No such process
```

The process does terminate properly though and the script waits for the app to exit before returning, the init script looks something like this... any ideas? I couldn't find anything online. Perhaps there is a better way to run java apps a daemon?

```

#! /bin/sh
# set the environment variables that are used
PATH=/sbin:/usr/sbin:/bin:/usr/bin
JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
JAVA=$JAVA_HOME/bin/java
JAVA_CLASSPATH=/var/lib/app/instance-common/lib/classes/resources:\
/var/lib/app/instance-common/lib/*:\
/var/lib/app/instance-common/lib/classes/*:\
/var/lib/app/instance-common/lib/jce/*:\
/var/lib/app/instance-common/lib/ext/*:\
/var/lib/app/instance-common/lib/endorsed/*:\
/var/lib/app/instance-common/lib/base/*
DESC="Application"
NAME="app-instance"
DAEMON=$JAVA
DAEMON_ARGS="-classpath $JAVA_CLASSPATH -Xms32m -Xmx512m class.class"
# uncomment for debugging
#DAEMON_ARGS="-Xrunjdwp:transport=dt_socket,server=y,address=9128,suspend=n $DAEMON_ARGS"
DAEMON_HOME="/etc/app/instance-engine"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/app-instance
#the user that will run the script
USER=app-instance
PROPERTIES_FILE=./conf/app.properties

# NO NEED TO MODIFY THE LINES BELOW

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	DAEMON_ARGS="$DAEMON_ARGS $PROPERTIES_FILE"
	
	start-stop-daemon -N -10 -b --start -d $DAEMON_HOME --quiet --chuid $USER -m -p $PIDFILE --exec $DAEMON -- $DAEMON_ARGS \
		|| return 2
		
	
	#Test to see if the engine has started
	start-stop-daemon -b --test --start -d $DAEMON_HOME --quiet --chuid $USER -m -p $PIDFILE --exec $DAEMON -- $DAEMON_ARGS >/dev/null 2>&1

    case "$?" in
        0) echo "[ FAIL ] Engine has not started";;
        1) echo "[ OK ] Engine has started";;
    esac				
}

#
# Function that stops the daemon/service
#
do_stop()
{
	start-stop-daemon --stop --retry 120 --oknodo --pidfile $PIDFILE
	RETVAL="$?"
	rm -f $PIDFILE
	return "$RETVAL"
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	echo "Starting $DESC" "$NAME"

	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1
				echo "[ FAIL ]";;		
	esac
	;;

  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	echo "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	echo "[ OK ]"
	;;
  restart)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	echo "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart}" >&2
	exit 3
	;;
esac

:

```

---

### Post by theolster on 2009-08-06
Did you solve this, I'm interested in writing a Java service - do you have any pointers?

---

