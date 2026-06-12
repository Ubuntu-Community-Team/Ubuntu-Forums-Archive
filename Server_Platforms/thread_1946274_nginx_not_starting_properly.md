---
title: "nginx not starting properly"
date: 2012-03-24
forum: Server Platforms
---

### Post by geudrik on 2012-03-24
I'm not entirely sure where I'm messing up here, but essentially I'm trying to use the start/stop daemon to start up nginx by using the following line...

```

start-stop-daemon: user '/etc/nginx/nginx.conf' not found
Command: start-stop-daemon --start --quiet --pidfile /var/run/nginx.pid --group nginx --exec /usr/local/nginx/sbin/nginx -c /etc/nginx/nginx.conf -v

```

As you can see from above, it's trying to pass the path to the config file as a user parameter.  Now, what is confusing me here that this single line is essentially two...
```

# I think this tells the daemon to do a few things (set the group for the --exec, make a pid etc)
start-stop-daemon --start --quiet --pidfile /var/run/nginx.pid --group nginx --exec

# This starts nginx and tell it which config to use, dumping a little verbose output
/usr/local/nginx/sbin/nginx -c /etc/nginx/nginx.conf -v

```

Anyone have any idea where I'm going wrong?

---

### Post by geudrik on 2012-03-27
As an update... when I run the following command..
```

$ sudo /etc/init.d/nginx --start
Starting nginx...
nginx version: nginx/1.0.14

Failed to load nginx. Daemon *NOT* started.

Command: --start --oknodo --pidfile /var/run/nginx.pid --startas /usr/local/nginx/sbin/nginx --chuid nginx -- -c /etc/nginx/nginx.conf -v

```

When I run just 
```

/usr/local/nginx/sbin/nginx -c /etc/nginx/nginx.conf -v

```

it dumps out 
```

Starting nginx...
nginx version: nginx/1.0.14

```

and promptly breaks, doesn't actually start or dump any other diagnostic information.

But the server isn't actually running. In fact, in the init script that I wrote, it even tells me that starting the server failed.  Any ideas?

Edit: I'm using start-stop-daemon in my init script.

---

### Post by geudrik on 2012-03-27
Solved.

```

#! /bin/sh

### BEGIN INIT INFO
# Provides:          nginx
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts the nginx web server
# Description:       starts nginx using start-stop-daemon
### END INIT INFO

## MAKE SURE YOUR BASE NGINX DIR IS LISTED HERE
PATH=/usr/local/nginx:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

## THIS IS THE ABSOLUTE PATH TO THE NGINX EXECUTABLE
DAEMON=/usr/local/nginx/sbin/nginx

## Username you want nginx to run as
NAME=nginx

## Process description you want to assign to nginx
DESC=nginx

## Options to pass to nginx - manual config location (see then nginx wiki for more options)
DAEMON_OPTS="-c /etc/nginx/nginx.conf"

test -x $DAEMON || exit 0

# Include nginx defaults if available
if [ -f /etc/default/nginx ] ; then
    . /etc/default/nginx
fi

set -e

. /lib/lsb/init-functions

case "$1" in
  start)
    echo -n "Starting $DESC: "
    start-stop-daemon --start --quiet --pidfile /usr/local/nginx/logs/$NAME.pid \
        --exec $DAEMON -- $DAEMON_OPTS || true
    echo "$NAME."
    ;;
  stop)
    echo -n "Stopping $DESC: "
    start-stop-daemon --stop --quiet --pidfile /usr/local/nginx/logs/$NAME.pid \
        --exec $DAEMON || true
    echo "$NAME."
    ;;
  restart|force-reload)
    echo -n "Restarting $DESC: "
    start-stop-daemon --stop --quiet --pidfile \
        /usr/local/nginx/logs/$NAME.pid --exec $DAEMON || true
    sleep 1
    start-stop-daemon --start --quiet --pidfile \
        /usr/local/nginx/logs/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS || true
    echo "$NAME."
    ;;
  reload)
      echo -n "Reloading $DESC configuration: "
      start-stop-daemon --stop --signal HUP --quiet --pidfile /usr/local/nginx/logs/$NAME.pid \
          --exec $DAEMON || true
      echo "$NAME."
      ;;
  status)
      status_of_proc -p /usr/local/nginx/logs/$NAME.pid "$DAEMON" nginx && exit 0 || exit $?
      ;;
  *)
    N=/etc/init.d/$NAME
    echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0

```

---

