---
title: "ISC dhcpd 4.0.1 init script"
date: 2009-06-23
forum: Server Platforms
---

### Post by ntheother on 2009-06-23
Hello Everyone,

I was disappointed to find that the dhcpd version included with the Ubuntu 8.04 edition was version 3. After checking the isc website I have found that version 3 practically at end of life. 

I took it upon myself to download, compile, and install the new version of isc dhcp (4.0.1). Everything was good, except for the init script, I had to change the current one to reflect the settings of the new dhcp configuration. 

I created this thread to share with you the init script and in hopes that others may also find it useful.

```
#!/bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin

test -f /usr/local/sbin/dhcpd || exit 0

. /lib/lsb/init-functions

# It is not safe to start if we don't have a default configuration...
if [ ! -f /etc/default/dhcpd ]; then
    usplash_write "QUIT"

    log_failure_msg "/etc/default/dhcpd does not exist! - Aborting..."
    exit 0
fi

# Default config file
CONFIG_FILE=/etc/dhcpd.conf

# Allow ltsp to override
if [ -f /etc/ltsp/dhcpd.conf ]; then
       CONFIG_FILE=/etc/ltsp/dhcpd.conf
fi

# Read init script configuration (so far only interfaces the daemon
# should listen on.)
. /etc/default/dhcpd

NAME=dhcpd
DESC="DHCP server"
DHCPDPID=/var/run/dhcpd/dhcpd.pid

test_config()
{
    if ! /usr/local/sbin/dhcpd -t -cf $CONFIG_FILE > /dev/null 2>&1; then
        echo "dhcpd self-test failed. Please fix the config file."
        echo "The error was: "
        /usr/local/sbin/dhcpd -t -cf $CONFIG_FILE 2>&1| sed '1,4d'
        exit 1
    fi
}

# single arg is -v for messages, -q for none
check_status()
{
    if [ ! -r "$DHCPDPID" ]; then
        test "$1" != -v || echo "$NAME is not running."
        return 3
    fi
    if read pid < "$DHCPDPID" && ps -p "$pid" > /dev/null 2>&1; then
        test "$1" != -v || echo "$NAME is running."
        return 0
    else
        test "$1" != -v || echo "$NAME is not running but $DHCPDPID exists."
        return 1
    fi
}

case "$1" in
    start)
        test_config

        # allow dhcp server to write lease and pid file
        mkdir -p /var/run/dhcpd
        chown dhcpd:dhcpd /var/run/dhcpd
        [ -e /var/db/dhcpd.leases ] || touch /var/db/dhcpd.leases
        chown dhcpd:dhcpd /var/db/dhcpd.leases
        if [ -e /var/db/dhcpd.leases~ ]; then
            chown dhcpd:dhcpd /var/db/dhcpd.leases~
        fi

        log_daemon_msg "Starting $DESC" "$NAME"
        start-stop-daemon --start --quiet --pidfile $DHCPDPID \
            --exec /usr/local/sbin/dhcpd -- -q -pf $DHCPDPID -cf $CONFIG_FILE $INTERFACES 
        sleep 2

        if check_status -q; then
            log_end_msg 0
        else
            log_end_msg 1
            exit 1
        fi
        ;;
    stop)
        log_daemon_msg "Stopping $DESC" "$NAME"
        start-stop-daemon --stop --quiet --pidfile $DHCPDPID
        log_end_msg $?
        rm -f "$DHCPDPID"
        ;;
    restart | force-reload)
        test_config
        $0 stop
        sleep 2
        $0 start
        if [ "$?" != "0" ]; then
            exit 1
        fi
        ;;
    status)
        echo -n "Status of $DESC: "
        check_status -v
        exit "$?"
        ;;
    *)
        echo "Usage: $0 {start|stop|restart|force-reload|status}"
        exit 1 
esac

exit 0
```

---

