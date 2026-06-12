---
title: "ushare won't autostart on ubuntu server 8.04"
date: 2009-03-19
forum: Server Platforms
---

### Post by Comandos on 2009-03-19
hello,
I am trying to set up a DLNA server. I use ushare and when ran manually it works great. However I don't seem to be able to autostart it. I wrote a script called ushare into /etc/init.d/ then made it executable, made the owner root and ran sudo update-rc.d ushare defaults but ushare still won't autostart on boot like I want. Here's the script I use:

> 
#!/bin/sh
### BEGIN INIT INFO
# Required-Start: $local_fs $syslog
# Required-Stop:
# Default-Start:  2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: start and stop ushare
# Description:
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/bin/ushare
NAME=ushare
DESC="uShare UPnP A/V Media Server"
PIDFILE=/var/run/ushare.pid

[ -r "/etc/ushare.conf" ] && . /etc/ushare.conf

# abort if no executable exists
[ -x $DAEMON ] || exit 0

# abort if no shared directory is defined
[ -z "$USHARE_DIR" ] && exit 0

set -e

checkpid() {
  [ -e $PIDFILE ] || touch $PIDFILE
}
case "$1" in
  start)
    echo -n "Starting $DESC: $NAME"
    checkpid
    start-stop-daemon --start --quiet --background --oknodo \
      --make-pidfile --pidfile $PIDFILE \
      --exec $DAEMON -- $USHARE_OPTIONS
    echo "."
  ;;
 stop)
    echo -n "Stopping $DESC: $NAME"
    start-stop-daemon --stop --signal 2 --quiet --oknodo --pidfile $PIDFILE
    echo "."
  ;;
  reload|force-reload)
    echo -n "Reloading $DESC: $NAME"
    start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile $PIDFILE --e$
    echo "."
  ;;
  reload|force-reload)
    echo -n "Reloading $DESC: $NAME"
    start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile $PIDFILE --e$
    echo "."
  ;;
  restart)
    $0 stop
    $1 start
  ;;
  *)
    N=/etc/init.d/$NAME
    echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
    exit 2
  ;;
esac

exit 0



I feel like I tried everything but for some reason I still can't get ushare starting on boot. Anyone knows what am I doing wrong?

PS
The script works, running
./ushare makes ushare run but for some reason it won't happen automaticly.

---

### Post by Jack1989 on 2009-03-19
Hi, I have a server running Ubuntu 8.04 with uShare. I think I just added a command to System -> Preferences -> Startup Programs

Maybe not so nice as yours, but it works for me!

---

### Post by Comandos on 2009-03-20
Thanks. I would have done that too only I have no GUI on my server, so I need a way to do it from there

---

