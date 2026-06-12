---
title: "Run Dynamips as a daemon service"
date: 2009-11-04
forum: Server Platforms
---

### Post by psypher on 2009-11-04
Hi All,

Please could someone assist with writing an init script for dynamips. We require this to be running as a service from start and be able to monitor with  monit and restart the service if the process fails.

Currently there is no init script for dynamips on ubuntu. Don't know why as the other dsitro's have them. I found the following article but it is very old and the script does not work: 

[http://7200emu.hacki.at/viewtopic.php?t=2198](http://7200emu.hacki.at/viewtopic.php?t=2198)

Please help pointing me in the right direction.

```
#!/bin/sh
# Start/stop the dynamips program as a daemon.
#
### BEGIN INIT INFO
# Provides: dynamips
# Default-Start: 2 3 4 5 95
# Default-Stop: 0 1 6 05
# Short-Description: Cisco Hardware Emulator daemon
### END INIT INFO

NAME="dynamips"
ALIES="dynamips_7201"
DAEMON=/usr/sbin/$NAME
PIDFILE=/var/run/$ALIES.pid
PORT=7201
DESC="Cisco Hardware Emulator"
SCRIPTNAME=/etc/init.d/$ALIES

test -f $DAEMON || exit 0
. /lib/lsb/init-functions

start() {
log_daemon_msg "Starting $DESC: $ALIES"
start-stop-daemon --start --chdir /opt/dynamips/ --background --make-pidfile --pidfile $PIDFILE --name $NAME --startas $DAEMON -- -H $PORT -l /var/log/$ALIES.log
log_end_msg $?
}
stop() {
log_daemon_msg "Stopping $DESC: $ALIES"
start-stop-daemon --stop --quiet --pidfile $PIDFILE --name $NAME
log_end_msg $?
}
reload() {
log_daemon_msg "Reloading $DESC: $ALIES"
start-stop-daemon --stop --retry 5 --quiet --pidfile $PIDFILE --name $NAME
start-stop-daemon --start --chdir /opt/dynamips/ --background --make-pidfile --pidfile $PIDFILE --name $NAME --startas $DAEMON -- -H $PORT -l /var/log/$ALIES.log
log_end_msg $?
}
status() {
status_of_proc -p $PIDFILE $DAEMON $NAME && exit 0 || exit $?
}

case "$1" in
start)
start
;;
stop)
stop
;;
restart)
stop
start
;;
reload)
reload
;;
condrestart)
if [ -f /var/lock/subsys/$ALIES ] ; then
stop
sleep 3
start
fi
;;
status)
status
;;
*)

log_action_msg "Usage: $SCRIPTNAME {start|stop|restart|condrestart|status}"
exit 2

esac
exit 0
```

Thanks

---

### Post by vint66 on 2009-12-06
Hi,

Your script should work fine on Ubuntu 9.04 or 9.10.

There is latest version of this script (but you need to adjust variables for your system):
```

#!/bin/sh
# Start/stop the dynamips program as a daemon.
#
### BEGIN INIT INFO
# Provides:          dynamips
# Default-Start:     2 3 4 5 95
# Default-Stop:      0 1 6 05
# Short-Description: Cisco Hardware Emulator daemon
### END INIT INFO

NAME="dynamips_7211"
ALIES="dynamips_7211"
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$ALIES.pid
PORT=7211
DESC="Cisco Hardware Emulator"
SCRIPTNAME=/etc/init.d/$ALIES
WORKDIR=/common/dynamips/$ALIES

test -f $DAEMON || exit 0
. /lib/lsb/init-functions

start()  {
    log_daemon_msg "Starting $DESC: $ALIES"
    start-stop-daemon --start --chdir $WORKDIR --background --make-pidfile --pidfile $PIDFILE --name $NAME --startas $DAEMON -- -H $PORT -l /var/log/$ALIES.log
    log_end_msg $? 
        }
stop()   {
    log_daemon_msg "Stopping $DESC: $ALIES"
    start-stop-daemon --stop --quiet --pidfile $PIDFILE --name $NAME
    log_end_msg $? 
        }
reload() {
    log_daemon_msg "Reloading $DESC: $ALIES"
    start-stop-daemon --stop --retry 5 --quiet --pidfile $PIDFILE --name $NAME
    start-stop-daemon --start --chdir $WORKDIR --background --make-pidfile --pidfile $PIDFILE --name $NAME --startas $DAEMON -- -H $PORT -l /var/log/$ALIES.log
    log_end_msg $?
    }
status() {
    status_of_proc -p $PIDFILE $DAEMON $NAME && exit 0 || exit $?
    }

case "$1" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    restart)
        stop
        start
        ;;
    reload)
        reload
        ;;
    status)
        status
        ;;
    *)

    log_action_msg "Usage: $SCRIPTNAME {start|stop|restart|status}"
    exit 2

esac
exit 0


```

---

### Post by Albert Net on 2010-02-26
Confirm vint66's code works on ubuntu 9.10.

Thank you for your effort.

---

