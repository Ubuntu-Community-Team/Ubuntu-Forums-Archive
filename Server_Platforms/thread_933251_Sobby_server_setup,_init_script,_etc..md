---
title: "Sobby server setup, init script, etc."
date: 2008-09-29
forum: Server Platforms
---

### Post by meonkeys on 2008-09-29
"[Sobby]("http://gobby.0x539.de/")" is a collaborative editing server to which Gobby clients can connect.

Anyone have tips for setting up a sobby server on Ubuntu 8.04.1? Installing the server binary is easy: ```
sudo apt-get install sobby
```

It's also quite easy to start the server manually as a non-root user, just run the sobby executable.

Setting up a daemon is a bit trickier. [I first tried using upstart]("https://answers.launchpad.net/upstart/+question/46662"), then decided to go for a standard SysV init script.

I added a sobby group and user, then created /var/lib/sobby for persistent data. Here's /etc/init.d/sobby: ```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          sobby
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Sobby Server
# Description:       Sobby is a collaborative editing server for Gobby clients
### END INIT INFO

# Sobby init script
#

set -e

[ -r /etc/default/sobby ] && . /etc/default/sobby

case "$SOBBY_ENABLE" in
	[Yy][Ee][Ss])
		;;
	*)
		exit 0
		;;
esac

# Defaults
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/sobby
PIDFILE=/var/run/sobby.pid
AUTOSAVE=/var/lib/sobby/autosave
SESSIONFILE=/var/lib/sobby/session
SOBBY_USER=sobby
SOBBY_GROUP=sobby
DESC="Sobby daemon: sobby"

OPTIONS="--autosave-file=$AUTOSAVE $SESSIONFILE $SOBBY_OPTIONS"

case "$1" in
	start)
		if [ ! -d /var/lib/sobby ]; then
			mkdir /var/lib/sobby
			chown $SOBBY_USER:root /var/lib/sobby
			chmod 755 /var/lib/sobby
		fi
		echo -n "Starting $DESC..."
		if LC_ALL=C start-stop-daemon --start \
		    --oknodo \
		    --pidfile $PIDFILE \
		    --make-pidfile \
		    --user $SOBBY_USER \
		    --chuid $SOBBY_USER:$SOBBY_GROUP \
		    --umask 002 \
		    --background \
		    --exec $DAEMON -- $OPTIONS >> /var/log/sobby 2>&1
		then
			echo "."
		else
			echo " (failed)."
			exit 1
		fi
		;;
	stop)
		echo -n "Stopping $DESC..."
		if start-stop-daemon --stop --quiet \
		    --oknodo \
		    --pidfile $PIDFILE \
		    --user $SOBBY_USER
		then
			rm -f $PIDFILE
			echo "."
		else
			echo " (failed)."
			exit 1
		fi
		;;
	restart|force-reload)
		sh $0 stop
		sleep 1
		sh $0 start
		;;
	status)
		echo -n "$DESC "
		if start-stop-daemon --stop --signal 0 --quiet \
		                     --pidfile $PIDFILE \
		                     --user $SOBBY_USER
		then
			echo "running"
			exit 0
		else
			if [ -e "$PIDFILE" ]
			then
				echo "failed"
				exit 1
			else
				echo "not running"
				exit 0
			fi
		fi
		;;
	*)
		echo "Usage: $0 {start|stop|restart|force-reload|status}"
		exit 1
		;;
esac

exit 0


```

Here's /etc/default/sobby: ```

# This file is sourced by /etc/init.d/sobby

# Set this variable to Yes if you want to run sobby at startup
SOBBY_ENABLE=Yes

# Additional options for the Sobby daemon
SOBBY_OPTIONS=""

```

I used update-rc.d to set up the S/K scripts.

This mostly seems to work. The only thing that doesn't work is logging.

---

### Post by freelook on 2008-12-22
Didn't work for me because the session file hadn't been created.  I had to add in this section:

```
        if [ ! -f $SESSIONFILE ]; then
            echo "Getting here"
            touch $SESSIONFILE
            chown $SOBBY_USER:root $SESSIONFILE
            chmod 644 $SESSIONFILE
        fi
```

right before the line:
         ```
echo -n "Starting $DESC..."
```

---

