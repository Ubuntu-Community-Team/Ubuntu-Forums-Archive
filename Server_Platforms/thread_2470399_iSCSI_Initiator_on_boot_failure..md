---
title: "iSCSI Initiator on boot failure."
date: 2021-12-28
forum: Server Platforms
---

### Post by roysen2 on 2021-12-28
I'm running Ubuntu Linux 20.04.3 as a headless server in a VM on TrueNAS. On my Ubuntu server, I'm running Nextcloud in docker and is it all working great. My problem started when I wanted to give Nextcloud access to my iSCSI drive (NTFS) that is shared from my TrueNAS. As I'm a newbie on running servers and had Webmin installed on my Ubuntu server I thought using Webmin to configure my iSCSI Initiator was wise. It worked well until my first reboot of Ubuntu. The iSCSI Initiator starts before my network so it will of course fail. Do you have some good advice since I'm sure it is an easy fix to my problem?

My /etc/init.d/open-iscsi:
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          open-iscsi iscsi
# Required-Start:    $network $local_fs iscsid
# Required-Stop:     $network $local_fs iscsid sendsigs
# Default-Start:     S
# Default-Stop:      0 1 6
# Short-Description: Login to default iSCSI targets
# Description:       Login to default iSCSI targets at boot and log out
#                    of all iSCSI targets at shutdown.
### END INIT INFO

PATH=/sbin:/bin
DAEMON=/sbin/iscsid
ADM=/sbin/iscsiadm
PIDFILE=/run/iscsid.pid
NAMEFILE=/etc/iscsi/initiatorname.iscsi
CONFIGFILE=/etc/iscsi/iscsid.conf
OMITDIR=/run/sendsigs.omit.d

[ -x "$DAEMON" ] || exit 0

. /lib/lsb/init-functions

# Include defaults if available
if [ -f /etc/default/open-iscsi ]; then
    . /etc/default/open-iscsi
fi


if [ ! -d /sys/class/ ]; then
  log_failure_msg "iSCSI requires a mounted sysfs, not started."
  exit 0
fi

RETVAL=0

start() {
    if ! [ -s $PIDFILE ] || ! kill -0 `sed -n 1p $PIDFILE` >/dev/null ; then
        log_failure_msg "iSCSI initiator daemon not started: not logging in to default targets"
        exit 1
    fi

    starttargets

    # activate LVM, mount filesystems, etc.
    /lib/open-iscsi/activate-storage.sh
}

starttargets() {
    log_daemon_msg "Setting up iSCSI targets"
    echo
    $ADM -m node --loginall=automatic
    log_end_msg 0
}

stoptargets() {
    log_daemon_msg "Disconnecting iSCSI targets"
    sync
    # only logout if daemon is running, iscsiadm hangs otherwise
        if [ -s $PIDFILE ] && kill -0 `sed -n 1p $PIDFILE` >/dev/null ; then
        /lib/open-iscsi/logout-all.sh
        fi

    log_end_msg 0
}

stop() {
    # Call umountiscsi.sh to unmount iSCSI devices first (always do
    # that, regardless of whether root is on iSCSI, umountiscsi.sh
    # will exclude it - and even if that shouldn't work, the mount
    # point will be busy)
    log_daemon_msg "Umounting iSCSI filesystems"
    /lib/open-iscsi/umountiscsi.sh
    umount_exit_status=$?
    log_end_msg $umount_exit_status

    if [ $umount_exit_status -ne 0 ]; then
        log_failure_msg "Couldn't unmount all iSCSI devices. not logging out from any target."
        exit 1
    fi

    stoptargets
}

restart() {
    stop
    start
}

restarttargets() {
    stoptargets
    starttargets
}

status() {
    #XXX FIXME: what to do here?
    #status iscsid
    # list active sessions
    echo Current active iSCSI sessions:
    $ADM -m session
}

case "$1" in
    start|starttargets|stop|stoptargets|restart|restarttargets|status)
        $1
        ;;
    force-reload)
        restart
        ;;
    *)
        echo "Usage: $0 {start|stop|restart|force-reload|status}"
        exit 1
        ;;
esac
exit $RETVAL
```

---

### Post by MAFoElffen on 2021-12-28
Disclaimer: I know just enough about this to be dangerous. I stumbled around this to make it work for me...

This was helpful to diagnose the connection:
[https://docs.oracle.com/cd/E23824_01/html/821-1459/fpjwy.html](https://docs.oracle.com/cd/E23824_01/html/821-1459/fpjwy.html)

When I was testing this, I made the same mistake as this person (post #7), not knowing where the pieces were supposed to be:
[https://forums.docker.com/t/solved-iscsi-login-fails-from-docker-plugin/68718/7](https://forums.docker.com/t/solved-iscsi-login-fails-from-docker-plugin/68718/7)

Option #3 of this, is how I finally got it to work:
[https://www.docker.com/blog/road-to-containing-iscsi/](https://www.docker.com/blog/road-to-containing-iscsi/)

In containers, there is a fine line of where it uses things from the container, or from the host... this was one where my problem/solution was on the host side of that line...

I hope this info helps...

---

### Post by roysen2 on 2021-12-29
> **MAFoElffen said:**
> 
Option #3 of this, is how I finally got it to work:
[https://www.docker.com/blog/road-to-containing-iscsi/](https://www.docker.com/blog/road-to-containing-iscsi/)

In containers, there is a fine line of where it uses things from the container, or from the host... this was one where my problem/solution was on the host side of that line...

I hope this info helps...
Thank you for the advice. "Option #3" is the way that I do it. But my problem is if I reboot my VM, then my iSCSI Initiator will start before my network is up and can of course not connect to my iSCSI server. The iSCSI Initiator is started from my init.d file at boot.

---

