---
title: "mysql stopping first than a service in init.d when shutdown or reboot"
date: 2012-12-23
forum: Server Platforms
---

### Post by cberni on 2012-12-23
In a "Ubuntu 12.04 LTS Server" I have a script in init.d and it is in the "update-rc.d SCRIPT_NAME defaults 98 02"

I need to stop this script FIRST than MYSQL... BUT mysql is always stopping first on shutdown or reboot. My script needs mysql turned on to stop in right way.

My script start with:
#!/bin/sh
#
### BEGIN INIT INFO
# Provides:          script
# Required-Start:    $ALL
# Required-Stop:     $ALL
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: test.
# Description:       test.
### END INIT INFO
#

The solution I found was editing the file /etc/init/mysql.conf changing the line below:
stop on **starting** rc RUNLEVEL=[016]
to
stop on **stopping **rc RUNLEVEL=[016]

I don't know if it is the right way to solve this problem. With this, mysql just turn off after all scripts in the old System V init System have completed stop (including my own script).

Is there another way (or righter way) to solve my problem when MYSQL could stop just AFTER my script have completed stopped?

---

### Post by craigp84 on 2012-12-24
Your current setup will work for this use case but as you suspected it has a gap. E.g. in the event you needed to go into single user mode (perhaps to do some filesystem maintenance tasks) your mysql instance would die abruptly when the network interfaces are shutdown - instead of mysql being shutdown gracefully before the network is shutdown (which happens just before entering single user mode).

You could move the script which needs to shutdown before mysql from the old rc.d and give it it's own upstart conf file. Then you could express the dependency either in the mysql file with something like ```
stop on stopped myscript
``` or in the myscript.conf file with ```
stop on stopping mysql
```

Hope this helps

---

### Post by cberni on 2013-01-21
craigp84,

the problem is DCM4CHEE (JBOSS) does not have a new Upstart (Ubuntu) scrip and I thing is too complicated create it. See bellow the current script.

Anymore help?



#!/bin/sh
#
# dcm4chee Control Script
#
# chkconfig: 3 80 20
# description: Start the DCM4CHEE DICOM Image Manager
#
# To use this script run it as root - it will switch to the specified user
# It loses all console output - use the log.
#
# Here is a little (and extremely primitive) startup/shutdown script
# for RedHat systems. It assumes that dcm4chee lives in /usr/local/dcm4chee,
# it's run by user 'pacs' and JDK binaries are in /usr/java/jdk/bin.
# All this can be changed in the script itself. 
#
# Either modify this script for your requirements or just ensure that
# the following variables are set correctly before calling the script.

#define where jboss is - this is the directory containing directories log, bin, conf etc
JBOSS_HOME=${JBOSS_HOME:-"/usr/local/dcm4chee"}

#define the user under which jboss will run, or use 'RUNASIS' to run as the current user
JBOSS_USER=${JBOSS_USER:-"pacs"}

#make sure java is in your path
JAVAPTH=${JAVAPTH:-"/usr/java/jdk/bin"}

#configuration to use, usually one of 'minimal', 'default', 'all'
JBOSS_CONF=${JBOSS_CONF:-"default"}

# JMX console credentials
JBOSS_ADMIN_USER=${JBOSS_ADMIN_USER:-"admin"}
JBOSS_ADMIN_PASS=${JBOSS_ADMIN_PASS:-"admin"}
ADMIN_USER_OPT="-u $JBOSS_ADMIN_USER"
ADMIN_PASS_OPT="-p $JBOSS_ADMIN_PASS"

#define the classpath for the shutdown class
JBOSSCP=${JBOSSCP:-"$JBOSS_HOME/bin/shutdown.jar:$JBOSS_HOME/client/jnet.jar"}

#define the script to use to start jboss
JBOSSSH=${JBOSSSH:-"$JBOSS_HOME/bin/run.sh -c $JBOSS_CONF"}

if [ "$JBOSS_USER" = "RUNASIS" ]; then
  SUBIT=""
else
  SUBIT="su - $JBOSS_USER -c "
fi

if [ -n "$JBOSS_CONSOLE" -a ! -d "$JBOSS_CONSOLE" ]; then
  # ensure the file exists
  touch $JBOSS_CONSOLE
  if [ ! -z "$SUBIT" ]; then
    chown $JBOSS_USER $JBOSS_CONSOLE
  fi 
fi

if [ -n "$JBOSS_CONSOLE" -a ! -f "$JBOSS_CONSOLE" ]; then
  echo "WARNING: location for saving console log invalid: $JBOSS_CONSOLE"
  echo "WARNING: ignoring it and using /dev/null"
  JBOSS_CONSOLE="/dev/null"
fi

#define what will be done with the console log
JBOSS_CONSOLE=${JBOSS_CONSOLE:-"/dev/null"}

JBOSS_CMD_START="cd $JBOSS_HOME/bin; $JBOSSSH"
JBOSS_CMD_STOP=${JBOSS_CMD_STOP:-"java -classpath $JBOSSCP org.jboss.Shutdown --shutdown $ADMIN_USER_OPT $ADMIN_PASS_OPT"}

if [ -z "`echo $PATH | grep $JAVAPTH`" ]; then
  export PATH=$PATH:$JAVAPTH
fi

if [ ! -d "$JBOSS_HOME" ]; then
  echo JBOSS_HOME does not exist as a valid directory : $JBOSS_HOME
  exit 1
fi

echo JBOSS_CMD_START = $JBOSS_CMD_START

case "$1" in
start)
    cd $JBOSS_HOME/bin
    if [ -z "$SUBIT" ]; then
        eval $JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &
    else
        $SUBIT "$JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &" 
    fi
    ;;
stop)
    if [ -z "$SUBIT" ]; then
        $JBOSS_CMD_STOP
    else
        $SUBIT "$JBOSS_CMD_STOP"
    fi 
    ;;
restart)
    $0 stop
    $0 start
    ;;
*)
    echo "usage: $0 (start|stop|restart|help)"
esac

---

### Post by cberni on 2013-01-30
ubuntuforums = don't work
ubuntuforums = no answer

---

