---
title: "VirtualBox startup script fails to wake guest when waking from sleep mode"
date: 2009-06-15
forum: Virtualisation
---

### Post by ktec on 2009-06-15
Hi there,

I have a virtual box guest which is configured to load on boot of the host, using the following script located in:

/etc/init.d/subtrac

```

#!/bin/sh
# Start/stop the Subtrac VM
#
### BEGIN INIT INFO
# Provides:          subtrac
# Required-Start:    $syslog $time vboxdrv vboxnet
# Required-Stop:     $syslog $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Subtrac in Virtualbox VM
# Description:       Subtrac in Virtualbox VM
### END INIT INFO

VBOXUSER=keith
VARRUNDIR=/var/run/VBoxHeadless
PIDFILE=$VARRUNDIR/subtrac.pid
VRDPADDR=192.168.0.5
VRDPPORT=4000

test -f /usr/bin/VBoxHeadless || exit 0

. /lib/lsb/init-functions
case "$1" in
start)   log_daemon_msg "Starting Subtrac in Virtualbox" "VBoxHeadless"
   mkdir -p $VARRUNDIR
   chgrp vboxusers $VARRUNDIR
   chmod g+ws $VARRUNDIR
        USER=$VBOXUSER LOGNAME=$VBOXUSER start-stop-daemon --start --quiet --bac
kground --make-pidfile --pidfile $PIDFILE --name VBoxHeadless --chuid $VBOXUSER 
--startas /usr/bin/VBoxHeadless -- -s subtrac
        log_end_msg $?
   ;;
stop)   log_daemon_msg "Stopping Subtrac in Virtualbox" "VBoxHeadless"
   su -c '/usr/bin/VBoxManage controlvm subtrac keyboardputscancode 1d 38 53' $V
BOXUSER
   sleep 30
   start-stop-daemon --stop --quiet --pidfile $PIDFILE --name VBoxHeadless
   rm -f $PIDFILE
        log_end_msg $?
        ;;
restart)
   $0 stop
   $0 start
   ;;
status)
   su -c '/usr/bin/VBoxManage showvminfo subtrac' $VBOXUSER | grep '^State:'
   ;;
*)   log_action_msg "Usage: /etc/init.d/subtrac {start|stop|restart|status}"
        exit 2
        ;;
esac
exit 0

```This is symbolically linked: /etc/rc2.d/S95subtrac to enable it to run at boot.

This seems to work fine, but I cobbled this together from various scripts found online so it might not be perfect.

The problem i have is when the host (which is a laptop) goes to sleep, and is then awoken, the guest is dead and requires a manual restart each time.

Is there anyone here who can tell me how to resolve this?

many thanks
keith:popcorn:

---

### Post by ghstridr on 2010-02-20
You need to look at the event mechanism of apm.  Go look at /etc/apm in the suspend.d and resume.d dirs. Then finally write your script to suspend/resume your running vbox machines via cmdline in the scripts.d dir.
There should be an example for alsa in there already.
When the laptop suspends the script will get run and run again when it resumes.

---

