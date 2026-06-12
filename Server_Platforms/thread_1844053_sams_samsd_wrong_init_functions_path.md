---
title: "sams samsd wrong init functions path"
date: 2011-09-14
forum: Server Platforms
---

### Post by vskog on 2011-09-14
I have a problem with restarting sams daemon.

My platform is:
Ubuntu Server 10.04 
apache 2.2.14 
mysql 5.1.41 
php 5.3.2 
squid 3.0 Stable 19 
sams-1.0.5 
Using as redirector: samsredir 
Auth type: ncsa  

After a long messing with my server I have managed to solve problem with unable to execute samsd in /etc/init.d/samsd 
(There was missing rights to execute it, solved it with chmod u+x /etc/init.d/samsd)  I have take samsd file from 
.../sams-1.0.5/etc/sams.debian
by using:
cp /home/user/sams-1.0.5/etc/sams.debian /etc/init.d/samsd  

When I've tried to restart it: 
/etc/init.d/samsd restart
It have said:
 .: 7: Can't open /etc/init.d/functions  
Hovewer in my samsd file was correct path: "/lib/lsb/init-functions"  

Later I have found wrong path: ". /etc/init.d/functions" in this file /etc/init.d/sams  
But when I have changed it to the correct one and tried to restart samsd it showd me this error: 
/etc/init.d# ./samsd restart 
Shutting down samsd: 
Starting samsd: /etc/init.d/sams: 58: daemon: not found  

There were no file in sams-1.0.5/etc/ which I can use to replace sams file from my /etc/init.d/ folder. 

Here is my sams and samsd files from /etc/init.d/:

sams:
```
#!/bin/sh
#
# chkconfig: 345 87 08
# description: Squid Account Management System (SAMS)
#
# Source function library.
. /etc/init.d/functions

SAMSPATH=`cat /etc/sams.conf | grep SAMSPATH | tr "SAMSPATH=" "\0"`
EXE=$SAMSPATH/bin/samsdaemon
LOCKFILE=/var/lock/samsd
RETVAL=0

start()
{
    echo -n "Starting samsd: "
    daemon "$EXE" 
    RETVAL=$?
    [ $RETVAL -eq 0 ] && touch "$LOCKFILE"
        echo
}

stop()
{
    echo -n "Shutting down samsd: "
    killproc "$EXE"
    RETVAL=$?
    [ $RETVAL -eq 0 ] && rm -f "$LOCKFILE"
        echo
}

restart()
{
    stop
    start
}

# See how we were called.
case "$1" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    restart)
        restart
        ;;
    reload)
        echo "Sams not implemented command yet"
        ;;
    status)
            status "$EXE"
        ;;
    *)
        echo "Usage: ${0##*/} {start|stop|restart}"
        RETVAL=1
esac

exit $RETVAL

```samsd:
```
#!/bin/sh -e

### BEGIN INIT INFO
# Provides:        sams
# Required-Start:    $local_fs $network $time
# Required-Stop:    
# Should-Start:        $named $mysql $squid
# Should-Stop:
# Default-Start:    2 3 4 5
# Default-Stop:        0 1 6
# Short-Description:    Starting sams daemon
# Description:        Squid Account Management System (SAMS)
#  Starting sams management daemon - samsdaemon
### END INIT INFO
#
# Author:    Pavel Vinogradov <Pavel.Vinogradov@nixdev.net>
#
# /etc/init.d/sams: start and stop the sams daemon

SAMSPATH=`cat /etc/sams.conf | grep SAMSPATH | tr "SAMSPATH=" "\0"`
NAME="sams"
DAEMON=$SAMSPATH/bin/samsdaemon
LOCKFILE=/var/lock/samsd
PIDFILE=/var/run/samsdaemon.pid
RETVAL=0
SAMS_ENABLE=true

test -x $DAEMON || exit 0

if ! [ -x "/lib/lsb/init-functions" ]; then
    . /lib/lsb/init-functions
else
    echo "E: /lib/lsb/init-functions not found, lsb-base (>= 3.0-6) needed"
    exit 1
fi

. /etc/default/rcS

case "$1" in 
    start)
        if "$SAMS_ENABLE"; then
            log_daemon_msg "Starting $NAME daemon" "$NAME"
            if [ -s $PIDFILE ] && kill -0 $(cat $PIDFILE) >/dev/null 2>&1; then
                log_progress_msg "apparently already running"
                log_end_msg 0
                exit 0
            fi
                  
            start-stop-daemon --start --quiet --background \
                --pidfile $PIDFILE \
                --exec $DAEMON
            RETVAL=$?
            [ $RETVAL -eq 0 ] && touch "$LOCKFILE"
            log_end_msg $RETVAL
        else
            [ "VERBOSE" != no ] && log_warning_msg "$NAME daemon not enabled, not starting..."
        fi
    ;;

    stop)
        if "$SAMS_ENABLE"; then
            log_daemon_msg "Stopping $NAME daemon" "$NAME"
            start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE 
            RETVAL=$?
            [ $RETVAL -eq 0 ] && rm -f "$LOCKFILE"
            log_end_msg $RETVAL
        else
            [ "VERBOSE" != no ] && log_warning_msg "$NAME daemon not enabled, not stoping..."
        fi
            
    ;;

    restart|force-reload)
        /etc/init.d/sams stop
        /etc/init.d/sams start
    ;;
    
    *)
        echo "Usage: ${0##*/} {start|stop|restart}"
        RETVAL=1
    ;;
esac

```  Any suggestions what I have done wrong?
*Sorry for bad English.

---

