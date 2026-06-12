---
title: "Caldavd working although init.d script fails"
date: 2009-11-10
forum: Server Platforms
---

### Post by novakry on 2009-11-10
Hi,

I've recently got a Caldav global calendar working, which I'm chuffed with. However I found that the script does not work when starting the caldav service. The strange thing is it does work when using stop and status within the script. 

I've done everything this guide says [https://wiki.ubuntu.com/CalendarServer]("https://wiki.ubuntu.com/CalendarServer")

Here is the script I'm using

```
#! /bin/sh

. /lib/lsb/init-functions

CALDAVD="/opt/caldavd/CalendarServer/run"
CALDAVD_USER="caldavd"
CALDAVD_OPTS="-d"
PIDFILE="/opt/caldavd/CalendarServer/logs/caldavd.pid"
NAME=caldavd

test -x $CALDAVD || exit 0

case "$1" in
  start)
        log_daemon_msg "Starting Darwin Calendar Server" "$NAME"
        if start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --chuid $CALDAVD_USER --exec $CALDAVD -- $CALDAVD_OPTS; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
        ;;
  stop)
        log_daemon_msg "Stopping Darwin Calendar Server" "$NAME"
        if start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
        ;;
  restart)
        log_daemon_msg "Restarting Darwin Calendar Server" "$NAME"
        start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile $PIDFILE
        if start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --chuid $CALDAVD_USER --exec $CALDAVD -- $CALDAVD_OPTS; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
        ;;
  status)
        status_of_proc -p "$CALDAVD" "$NAME" && exit 0 || exit $?
        ;;
  *)
        log_action_msg "Usage: /etc/init.d/caldavd {start|stop|restart|status}"
        exit 1
esac

exit 0
```

Please Help

N

---

