---
title: "how do i start JBoss automatically on boot?"
date: 2007-07-05
forum: Server Platforms
---

### Post by g[r]eek on 2007-07-05
attention all linux groksters:

i've installed everything correctly (ubuntu server, java, jboss). now i'm wanting to have jboss load up automatically when i boot up ubuntu. i know i need to make an '/etc/init.d/jboss' type startup script, but i have no clue when it comes to writing such scripts.

can someone please provide me with a startup/boot script for jboss application server?

also please provide the various S/K scripts for all the different run levels.

i wish there was an easy X-step process to doing this outlined somewhere on the web. i haven't been able to find such a tutorial.

cheers

---

### Post by scragar on 2007-07-05
System > Preferences > Sessions

Start-up Programs

Add

type: "/etc/init.d/jboss" into the box.

click OK.

Click close.

was that really that hard?

---

### Post by g[r]eek on 2007-07-05
scragar, thanks for taking the time to answer my post. however your advice is not what i had in mind. perhaps i was a tad elusive with my first post. i'll try be more explicit.

1. i am using dapper drake 6.06 server edition. it is command-line only.
2. i have created the '/etc/init.d/jboss' file.
3. i have made this same file executable, as required.
4. i have also registered this startup script with rc.local so that it is initiated at the various run-levels (mainly run-level 3, for multi-user mode; which i am assuming is default for server installations).

my point here is that i have no problem finding my way around the operating system, nor do i need assistance in creating files/scripts etc.

what i am looking for, is the actual content of this '/etc/init.d/jboss' startup script. i am no expert in writing such daemon-type startup scripts. i have found a couple of example startup scripts for jboss, but they are designed with red-hat in mind.

so my question, in a nut-shell, is does anyone here run jboss application server on their ubuntu server, and if so, what is the content of your '/etc/init.d/jboss' file?

i wish it was as simple as executing '$JBOSS_HOME/bin/run.sh' but anyone who has written startup scripts in the past will know that this simply won't suffice. also i need to know what the kill script's content should be when shutting down.

thanks.

---

### Post by g[r]eek on 2007-07-05
i have found this link which seems to provide a good solution for all linux platforms. i figured i'd add it here since it may prove useful to others.

[http://wiki.jboss.org/wiki/Wiki.jsp?page=StartJBossOnBootWithLinux](http://wiki.jboss.org/wiki/Wiki.jsp?page=StartJBossOnBootWithLinux)

cheers.

---

### Post by Bokonon on 2007-08-10
I used the redhat startup script and made a few changes.  Username/password were about all I think.  It is located in your JBOSS_HOME/bin directory.

Setup JBOSS_HOME and JAVA_HOME, but I assume you already have that.

Works just fine.

---

### Post by orotrev on 2007-08-10
I also had success with tweaking the Red Hat script.

---

### Post by freecouch on 2008-04-29
Here is a working init.d script on Ubuntu 8.04.  Change the "CHANGE..." sections to values appropriate for your setup.

```

#!/bin/sh
#
# $Id: jboss_init_redhat.sh 60992 2007-02-28 11:33:27Z dimitris@jboss.org $
#
# JBoss Control Script
#
# To use this script run it as root - it will switch to the specified user
#
# Here is a little (and extremely primitive) startup/shutdown script
# for RedHat systems. It assumes that JBoss lives in /usr/local/jboss,
# it's run by user 'jboss' and JDK binaries are in /usr/local/jdk/bin.
# All this can be changed in the script itself.
#
# Either modify this script for your requirements or just ensure that
# the following variables are set correctly before calling the script.

#define where jboss is - this is the directory containing directories log, bin, conf etc
JBOSS_HOME=${JBOSS_HOME:-"[CHANGE_TO_YOUR_JBOSS_HOME]"}

#define the user under which jboss will run, or use 'RUNASIS' to run as the current user
JBOSS_USER=${JBOSS_USER:-"[CHANGE_TO_YOUR_JBOSS_USER]"}

#make sure java is in your path
JAVAPTH=${JAVAPTH:-"[CHANGE_TO_YOUR_JAVA_HOME]/bin"}

#configuration to use, usually one of 'minimal', 'default', 'all'
JBOSS_CONF=${JBOSS_CONF:-"default"}

#if JBOSS_HOST specified, use -b to bind jboss services to that address
JBOSS_BIND_ADDR=${JBOSS_HOST:+"-b $JBOSS_HOST"}

#define the classpath for the shutdown class
JBOSSCP=${JBOSSCP:-"$JBOSS_HOME/bin/shutdown.jar:$JBOSS_HOME/client/jnet.jar"}

#define the script to use to start jboss
JBOSSSH=${JBOSSSH:-"$JBOSS_HOME/bin/run.sh -c $JBOSS_CONF $JBOSS_BIND_ADDR"}

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
#JBOSS_CONSOLE=${JBOSS_CONSOLE:-"/dev/null"}
JBOSS_CONSOLE=${JBOSS_CONSOLE:-"$JBOSS_HOME/log/console.log"}

JBOSS_CMD_START="cd $JBOSS_HOME/bin; $JBOSSSH"
JBOSS_CMD_STOP=${JBOSS_CMD_STOP:-"$JAVAPTH/java -classpath $JBOSSCP org.jboss.Shutdown --shutdown"}

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


```

---

