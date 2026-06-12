---
title: "After boot, have to restart /etc/init.d/mdadm"
date: 2009-02-15
forum: Server Platforms
---

### Post by thornomad on 2009-02-15
Hi - 

I'm not sure how to troubleshoot this problem and wondered if someone could help.

After I reboot my system, I have to "restart" /etc/init.d/mdadm in order for the monitoring to work as intended (I have a script run every time their is an event).  I am afraid that one of these days, I will forget to restart it after a reboot and I won't be notified of any disk failures.

After poking around a bit, I have found that after a reboot /etc/init.d/mdadm *is* running -- it's just that my monitoring tool isn't being invoked.  I know this because if I try to start it I get this:

```
$ sudo /etc/init.d/mdadm start
 * Starting MD monitoring service mdadm --monitor
/sbin/mdadm already running.
   ...fail!

```

But, despite the fact that it has started, when I test my raid devices by setting them as faulty, I don't get any notifications; however, after I run this:

```
$ sudo /etc/init.d/mdadm restart
 * Stopping MD monitoring service mdadm --monitor
   ...done.
 * Starting MD monitoring service mdadm --monitor
   ...done.
```

Then all notifications work as expected.  

My only thought is maybe the monitoring is coming up before the raid devices, or something, so that it doesn't see them -- I'm just not sure how to troubleshoot it.

Here is the body of the startup script, if anyone has any ideas I would love to try them!  I know I could probably do a work around (like write my own startup script that restarts the script) but that seems like a hack -- would rather figure out what is going on.

Thanks.

```
$ cat /etc/init.d/mdadm 
#!/bin/sh
#
# Start the MD monitor daemon for all active MD arrays if desired.
#
# Copyright © 2001-2005 Mario Jou/3en <joussen@debian.org>
# Copyright © 2005-2007 Martin F. Krafft <madduck@debian.org>
# Distributable under the terms of the GNU GPL version 2.
#
# $Id$
#
### BEGIN INIT INFO
# Provides:          mdadm
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: MD monitoring daemon
# Description:       mdadm provides a monitor mode, in which it will scan for
#                    problems with the MD devices. If a problem is found, the
#                    administrator is alerted via email, or a custom script is
#                    run.
### END INIT INFO

set -eu

MDADM=/sbin/mdadm
RUNDIR=/var/run/mdadm
PIDFILE=$RUNDIR/monitor.pid
DEBIANCONFIG=/etc/default/mdadm

test -x "$MDADM" || exit 0

test -f /proc/mdstat || exit 0

START_DAEMON=true
test -f $DEBIANCONFIG && . $DEBIANCONFIG

. /lib/lsb/init-functions

is_true()
{
  case "${1:-}" in
    [Yy]es|[Yy]|1|[Tt]|[Tt]rue) return 0;;
    *) return 1;
  esac
}

case "${1:-}" in
  start)
    if is_true $START_DAEMON; then
      log_daemon_msg "Starting MD monitoring service" "mdadm --monitor"
      mkdir -p $RUNDIR
      set +e
      start-stop-daemon -S -p $PIDFILE -x $MDADM -- \
        --monitor --pid-file $PIDFILE --daemonise --scan ${DAEMON_OPTIONS:-}
      log_end_msg $?
      set -e
    fi
    ;;
  stop)
    if [ -f $PIDFILE ] ; then
      log_daemon_msg "Stopping MD monitoring service" "mdadm --monitor"
      set +e
      start-stop-daemon -K -p $PIDFILE -x $MDADM
      rm -f $PIDFILE
      log_end_msg $?
      set -e
    fi
    ;;
  restart|reload|force-reload)
    ${0:-} stop
    ${0:-} start
    ;;
  *)
    echo "Usage: ${0:-} {start|stop|restart|reload|force-reload}" >&2
    exit 1
    ;;
esac

exit 0
```

---

