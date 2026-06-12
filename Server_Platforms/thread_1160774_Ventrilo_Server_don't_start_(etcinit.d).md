---
title: "Ventrilo Server don't start (/etc/init.d)"
date: 2009-05-16
forum: Server Platforms
---

### Post by crash748 on 2009-05-16
[Ubuntu 9.04]  
 [Ventrilo 2.3.1]  

 Hello!  
        That makes two days that I find a way to make my startup scripts work when my server boot. If I run my scripts every things are perfect but when the server startup it was something else. I know they are run because my _.pid files are create at the same time the server start. They are started and stop immediately! 

    I am new in the bash world, I missed something but I do not know what!  

 Here my /etc/init.d/ventrilo```

#!/bin/sh -e

PATH=/sbin:/bin:/usr/sbin:/usr/bin
SCRIPT_NAME="ventrilo"
SOFT_PATH="/project/scripts/"
SOFT_START="start_ventrilo"
SOFT_STOP="stop_ventrilo"

[ -x $SOFT_PATH$SOFT_START ] || exit 0
[ -x $SOFT_PATH$SOFT_STOP ] || exit 0

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions


case "$1" in
start)
    echo Please wait
        $SOFT_PATH$SOFT_START &
    sleep 3s
        exit 0
;;
stop)
    echo Please wait!
    $SOFT_PATH$SOFT_STOP &
    sleep 3s
        exit 0
;;
restart)
    $SOFT_PATH$SOFT_STOP &
    sleep 1s
    echo Please wait! Process will restart soon!
    sleep 1s
        echo 3
        sleep 1s
        echo 2
        sleep 1s
        echo 1
        sleep 1s
    $SOFT_PATH$SOFT_START &
    sleep 3s
        exit 0
;;
*)
    echo "Usage: /etc/init.d/$SCRIPT_NAME {start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```It was activated with the command ==> update-rc.d ventrilo start 99 2 3 4 5. stop 20 0 1 6.
 

The script "/project/scripts/start_ventrilo" is a keepalive for the ventrilo application.
But at the server boot, the script and the ventrilo server are run and stop! I don't understand! 

Here my keepalive script  /project/scripts/start_ventrilo
```

#!/bin/bash

if [[ `whoami` != "root" ]]; then
    echo
    echo "Must be root to run this script."
    sleep 1s
    exit 0
fi

RUN_USER="ripou"
SOFT_PATH="/project/ventrilo/"
SOFT_NAME="ventrilo_srv"
SOFT_CMD="-f/project/ventrilo/ventrilo_srv"
SOFT_PID_FILE=$SOFT_PATH$SOFT_NAME"_soft_.pid"
SCRIPT_PID_FILE=$SOFT_PATH$SOFT_NAME"_script_.pid"

if [ -e $SCRIPT_PID_FILE ]; then
    SCRIPT_PID=$(cat $SCRIPT_PID_FILE)
    if [[ `ps -A | grep $SCRIPT_PID` ]] ; then
            echo
        echo Script is already running!
        if [ -e $SOFT_PID_FILE ] ; then
                SOFT_PID=$(cat $SOFT_PID_FILE)
            if [[ `ps -A | grep $SOFT_PID` ]] ; then
                            echo $SOFT_NAME is already running
            else
                echo $SOFT_NAME is not running
            fi
        fi
        sleep 1s
        exit 0
    else
        SCRIPT_PID=$$
        echo $SCRIPT_PID > $SCRIPT_PID_FILE
    fi
else
        SCRIPT_PID=$$
        echo $SCRIPT_PID > $SCRIPT_PID_FILE
fi

if [ -e $SOFT_PID_FILE ] ; then 
    SOFT_PID=$(cat $SOFT_PID_FILE)
fi
while  [ 1 == 1 ] ; do
    if [ -e $SOFT_PID_FILE ]; then
        if [[ `ps -A | grep $SOFT_PID` ]] ; then
                echo
                echo $SOFT_NAME is already running
        else
            su $RUN_USER -c "$SOFT_PATH$SOFT_NAME $SOFT_CMD" &
            SOFT_PID=$!
            echo $SOFT_PID > $SOFT_PID_FILE
                  echo
            echo $SOFT_NAME is starting
        fi
    else
                su $RUN_USER -c "$SOFT_PATH$SOFT_NAME $SOFT_CMD" &
                SOFT_PID=$!
                echo $SOFT_PID > $SOFT_PID_FILE
                echo
                echo $SOFT_NAME is starting
    fi
    while [[ `ps -A | grep $SOFT_PID` ]] ; do
        sleep 1m
    done 
        echo
        echo "$SOFT_NAME crashed, restarting in 5 seconds.."
        echo 5
        sleep 1s
        echo 4
        sleep 1s
        echo 3
        sleep 1s        
        echo 2
        sleep 1s
        echo 1
        sleep 1s
        echo "Restarting.."
        echo
done

```If somebody could help find the problem, it will be really appreciate!

---

### Post by llamaX on 2009-05-16
A couple thoughts:

[LIST]
[*]You seem to be using exit 0 for the script bailing, while this is generally used to show a successful script completion.
[*]The keep-alive script really shouldn't start your app; the init script should.
[/LIST]
Here's a simple, untested, replacement:
```

#!/bin/bash

if [ $UID -ne 0 ]; then
    echo "Must be root to run this script."
    exit 1
fi

while [ 1 ]; do
    if [ ! pgrep ventrilo_srv ]; then
        /etc/init.d/ventrilo restart
    else
        sleep 60
    fi
done

exit 0

```Likelywise, here's a simple, untested, init.d replacement (based off lighttpd's):
```

#!/bin/bash
### BEGIN INIT INFO
# Provides:          ventrilo
# Required-Start:    networking
# Required-Stop:     networking
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start the ventrilo communications server.
### END INIT INFO

DAEMON=/project/scripts/ventrilo_srv
NAME=ventrilo
DESC="Communications Server"
PIDFILE=/projects/scripts/vent.pid
SSD=/sbin/start-stop-daemon
KEEPALIVE=/projects/scripts/vent-check.sh

DAEMON_OPTS="-f$DAEMON"

case "$1" in
    start)
        log_daemon_msg "Starting $DESC" $NAME
        if ! start-stop-daemon --start --quiet\
        --pidfile $PIDFILE --exec $DAEMON -- $DAEMON_OPTS ; then
            log_end_msg 1
        else
            log_end_msg 0
            $KEEPALIVE
        fi
        ;;
    stop)
        log_daemon_msg "Stopping $DESC" $NAME
        if $SSD --quiet --stop --oknodo --retry 30\
        --pidfile $PIDFILE --exec $DAEMON; then
            rm -f $PIDFILE
            killall $KEEPALIVE
            log_end_msg 0
        else
            log_end_msg 1
        fi
        ;;
    restart|force-reload)
        $0 stop
        [ -r  $PIDFILE ] && while pidof ventrilo_srv |\
                 grep -q `cat $PIDFILE 2>/dev/null` 2>/dev/null ; do sleep 1; done
        $0 start
        ;;
    *)
        echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```Hope this helps.  Good luck.

---

### Post by crash748 on 2009-05-16
Hi, llamaX 
You have make sunshine in my day!:p

I prefer the script the maner you propose to do it, simple, clear and working!

Your method is the way it should be! 

Thank you! Very much!):P

---

