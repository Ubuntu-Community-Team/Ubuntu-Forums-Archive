---
title: "Samba4 as DC daemon not starting at boot"
date: 2013-04-04
forum: Server Platforms
---

### Post by Toxic64 on 2013-04-04
Hi everyone, 

I have recently installed Samba4 via Git (v4.0.4) as an AD DC and everything works perfectly fine untill reboot.

Samba4 daemon doesn't start (I have to start it manually).
 I have tried all available scripts I could find from the ones that can be found here [https://wiki.samba.org/index.php/Samba4/InitScript](https://wiki.samba.org/index.php/Samba4/InitScript)to the ones that can be found on various Ubuntu/Samba4 forums.

Still no Luck actually.

Last one I tried is the debian/samba4 startup script hoping for more luck...  doesn't help much...

The current script I'm on is this one
```

#! /bin/sh

### BEGIN INIT INFO
# Provides:          samba4
# Required-Start:    $network $local_fs $remote_fs
# Required-Stop:     $network $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: start Samba daemons 
### END INIT INFO

#
# Start/stops the Samba daemon (samba).
# Adapted from the Samba 3 packages.
#

PIDDIR=/var/run/samba
SAMBAPID=$PIDDIR/samba.pid

# clear conflicting settings from the environment
unset TMPDIR

# See if the daemon and the config file are there
test -x /usr/sbin/samba -a -r /etc/samba/smb.conf || exit 0

. /lib/lsb/init-functions

case "$1" in
    start)
        log_daemon_msg "Starting Samba 4 daemon" "samba"
        # Make sure we have our PIDDIR, even if it's on a tmpfs
        install -o root -g root -m 755 -d $PIDDIR

        if ! start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/samba -- -D; then
            log_end_msg 1
            exit 1
        fi

        log_end_msg 0
        ;;
    stop)
        log_daemon_msg "Stopping Samba 4 daemon" "samba"

        start-stop-daemon --stop --quiet --name samba $SAMBAPID
        # Wait a little and remove stale PID file
        sleep 1
        if [ -f $SAMBAPID ] && ! ps h `cat $SAMBAPID` > /dev/null
        then
            # Stale PID file (samba was succesfully stopped),
            # remove it (should be removed by samba itself IMHO.)
            rm -f $SAMBAPID
        fi

        log_end_msg 0

        ;;
    restart|force-reload)
        $0 stop
        sleep 1
        $0 start
        ;;
    *)
        echo "Usage: /etc/init.d/samba {start|stop|restart|force-reload}"
        exit 1
        ;;
esac

exit 0

```

when samba 4 is started via ```
sudo service samba start
```
no **samba.pid** file creates in ```
/var/run/samba
``` there is one **samba.pid** in```
 /usr/local/samba/var/run
``` though

Has anyone had this problem /solved it by any luck?

---

### Post by Toxic64 on 2013-04-10
Ok I finally solved it myself. for those of you who would find this behaviour:
just put this samba.conf file in /etc/init/
```
description "SMB/CIFS File and Active Directory Server"
author      "Jelmer Vernooij <jelmer@ubuntu.com>"
start on (local-filesystems and net-device-up)
stop on runlevel [!2345]
expect fork
normal exit 0
pre-start script
    [ -r /etc/default/samba4 ] && . /etc/default/samba4
    install -o root -g root -m 755 -d /var/run/samba
    install -o root -g root -m 755 -d /var/log/samba
end script
exec /usr/local/samba/sbin/samba -D
```

then 

```
chmod 755 /etc/init/samba4.conf
```

reboot to test.

---

