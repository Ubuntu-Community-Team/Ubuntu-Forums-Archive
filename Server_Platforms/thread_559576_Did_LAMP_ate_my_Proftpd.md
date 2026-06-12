---
title: "Did LAMP ate my Proftpd?"
date: 2007-09-25
forum: Server Platforms
---

### Post by legolas on 2007-09-25
It seems I just got my proftpd working.   I used Frodons wonderful howto:
[http://ubuntuforums.org/showthread.php?t=79588&highlight=proftpd+server](http://ubuntuforums.org/showthread.php?t=79588&highlight=proftpd+server)
I installed LAMP using the ubuntu documentation and I tried to start up my proftpd and it said
sudo: /etc/init.d/proftpd: command not found
I checked the folder and it is gone!  Did the LAMP eat it?  I am a complete newbie, but I am doing my best to start up a web server.  As soon as I can figure out what happened, the lesson will be well learned, however, right now I have no idea.  Any thoughts guys?  Thanks

---

### Post by pheeror on 2007-09-25
What was you trying to say with words "I installed LAMP".
```

$ aptitude search lamp
p   lampython                                    - MPI-enhanced Python interpreter (LAM based version) 

```

---

### Post by legolas on 2007-09-25
Sorry for not being clear.  I installed the LAMP server using:
sudo tasksel install lamp-server
from
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by pheeror on 2007-09-26
It's really wierd, if this really wipe your init.d/proftpd out. 
Anyway, you can install proftpd
```

aptitude install proftpd

```
If this doesn't help, backup /etc/proftpd, purge proftpd, install proftpd, move backuped proftpd config back.

Of course, the most easyist way is just copy /etc/init.d/proftpd from another machine. There is mine (1.3.0-24ubuntu1).
```

#!/bin/sh 

# Start the proftpd FTP daemon.

PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/sbin/proftpd
NAME=proftpd

# Defaults
RUN="no"
OPTIONS=""

PIDFILE=`grep -i 'pidfile' /etc/proftpd/proftpd.conf | sed -e 's/pidfile[\t ]\+//i'`
if [ "x$PIDFILE" = "x" ];
then
	PIDFILE=/var/run/proftpd.pid
fi

# Read config (will override defaults)
[ -r /etc/default/proftpd ] && . /etc/default/proftpd

trap "" 1
trap "" 15

test -f $DAEMON || exit 0

#
# These compatibility funcs are here just for sarge backports.
# They will be removed post-etch.
#
log_daemon_msg() {
    echo -n "$1: $2"
}

log_end_msg() {
    if [ $1 -ne 0 ]; then
       echo " failed!"
    else
       echo "."
    fi
}

[ -f /lib/lsb/init-functions ] && . /lib/lsb/init-functions

#
# Servertype could be inetd|standalone|none.
# In all cases check against inetd and xinetd support.
#
if ! egrep -qi "^[[:space:]]*ServerType.*standalone" /etc/proftpd/proftpd.conf
then
    if [ $(dpkg-divert --list xinetd|wc -l) -eq 1 ] 
    then
	if egrep -qi "server[[:space:]]*=[[:space:]]*/usr/sbin/proftpd" /etc/xinetd.conf 2>/dev/null || \
	   egrep -qi "server[[:space:]]*=[[:space:]]*/usr/sbin/proftpd" /etc/xinetd.d/* 2>/dev/null
	then
    		RUN="no"
    		INETD="yes"
	else
		if ! egrep -qi "^[[:space:]]*ServerType.*inetd" /etc/proftpd/proftpd.conf
		then
    			RUN="yes"
			INETD="no"
		else
			RUN="no"
			INETD="no"
		fi
	fi
    else
    	if egrep -qi "^ftp.*/usr/sbin/proftpd" /etc/inetd.conf 2>/dev/null
    	then
    		RUN="no"
    		INETD="yes"
    	else
		if ! egrep -qi "^[[:space:]]*ServerType.*inetd" /etc/proftpd/proftpd.conf
		then
    			RUN="yes"
			INETD="no"
		else
			RUN="no"
			INETD="no"
		fi
    	fi
    fi
fi

# /var/run could be on a tmpfs

[ ! -d /var/run/proftpd ] && mkdir /var/run/proftpd

start()
{
    log_daemon_msg "Starting ftp server" "$NAME"

    start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $DAEMON -- $OPTIONS  
    if [ $? != 0 ]; then
        log_end_msg 1
        exit 1
    else
        log_end_msg 0
    fi
}

signal()
{

    if [ "$1" = "stop" ]; then
	SIGNAL="TERM"
    	log_daemon_msg "Stopping ftp server" "$NAME"
    else
	if [ "$1" = "reload" ]; then
	    SIGNAL="HUP"
    	    log_daemon_msg "Reloading ftp server" "$NAME"
	else
	    echo "ERR: wrong parameter given to signal()"
	    exit 1
	fi
    fi
    if [ -f "$PIDFILE" ]; then
    	start-stop-daemon --stop --signal $SIGNAL --quiet --pidfile "$PIDFILE"
   	 if [ $? = 0 ]; then
        	log_end_msg 0
    	else
		SIGNAL="KILL"
		start-stop-daemon --stop --signal $SIGNAL --quiet --pidfile "$PIDFILE"
    		if [ $? != 0 ]; then
        		log_end_msg 1
        		[ $2 != 0 ] || exit 0
    		else
        		log_end_msg 0
    		fi
    	fi
   	if [ "$SIGNAL" = "KILL" ]; then
		rm -f "$PIDFILE"
    	fi
    else
        log_end_msg 0
    fi
}

case "$1" in
    start)
	if [ "x$RUN" = "xyes" ] ; then
	    start
	else
	    if [ "x$INETD" = "xyes" ] ; then
		echo "ProFTPd is started from inetd/xinetd."
	    else 
	    	echo "ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration."
	    fi
	fi
	;;

    force-start)
	if [ "x$INETD" = "xyes" ] ; then
	    echo "Warning: ProFTPd is started from inetd/xinetd (trying to start anyway)."
	fi
	start
	;;	
    
    stop)
	if [ "x$RUN" = "xyes" ] ; then
	    signal stop 0
	else
	    if [ "x$INETD" = "xyes" ] ; then
		echo "ProFTPd is started from inetd/xinetd."
	    else 
	    	echo "ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration."
	    fi
	fi
	;;

    force-stop)
	if [ "x$INETD" = "xyes" ] ; then
	    echo "Warning: ProFTPd is started from inetd/xinetd (trying to kill anyway)."
	fi
	signal stop 0
	;;

    reload)
	signal reload 0
	;;

    force-reload|restart)
	if [ "x$RUN" = "xyes" ] ; then
	    signal stop 1
	    sleep 2
	    start
	else
	    if [ "x$INETD" = "xyes" ] ; then
		echo "ProFTPd is started from inetd."
	    else 
	    	echo "ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration."
	    fi
	fi
	;;

    *)
	echo "Usage: /etc/init.d/$NAME {start|force-start|stop|force-stop|reload|restart|force-reload}"
	exit 1
	;;
esac

exit 0

```

---

### Post by legolas on 2007-09-28
It took me a real long time to get it all configured, just to have the LAMP install destroy it.  Bummer.  Thanks for your help pheeror.

---

