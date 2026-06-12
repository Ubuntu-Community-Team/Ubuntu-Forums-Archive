---
title: "Bind won't start"
date: 2005-12-15
forum: Server Platforms
---

### Post by nimy on 2005-12-15
I had problems getting bind to start with 
/etc/init.d/bind9 start until I found out that the error log was at /var/log/syslog 
(was looking for redhat location)
I was happy to find that to run the process as bind, all I had to do was chown /etc/bind files :) 

Now I would like to create a named system account with home dir at /var/named and move /etc/bind files there and of course chown them.  I assume that to get bind9 to start under this config, I'll have to change something else, like maybe /etc/default/bind9, but I don't know.  

Pls advise, thanks!  The reason I need to do this is that I have a RHES server as my primary DNS (paid for), and I'd like to run ubuntu as my alternate DNS (free).

I don't know if it can work because DNS for each host is set up differently.  For example, ubuntu doesn't use the controls option for the rcndkey that are present in redhat's named.conf.  Why?

---

### Post by diebels on 2005-12-15
Here's a good one:
> **http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3]
DNS-Server

```
apt-get install bind9
```

For security reasons we want to run BIND chrooted so we have to do the following steps:

```
/etc/init.d/bind9 stop
```

Edit the file /etc/default/bind9 so that the daemon will run as the unprivileged user 'bind', chrooted to /var/lib/named. Modify the line: OPTS="-u bind" so that it reads OPTIONS="-u bind -t /var/lib/named":

OPTIONS="-u bind -t /var/lib/named"

Create the necessary directories under /var/lib:

```
mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run
```

Then move the config directory from /etc to /var/lib/named/etc:

```
mv /etc/bind /var/lib/named/etc
```

Create a symlink to the new config directory from the old location (to avoid problems when bind is upgraded in the future):

```
ln -s /var/lib/named/etc/bind /etc/bind
```

Make null and random devices, and fix permissions of the directories:

```
mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind
```

We need to modify the startup script /etc/init.d/sysklogd of sysklogd so that we can still get important messages logged to the system logs. Modify the line: SYSLOGD="-u syslog" so that it reads: SYSLOGD="-u syslog -a /var/lib/named/dev/log":

```

# /etc/init.d/sysklogd: start the system log daemon.

PATH=/bin:/usr/bin:/sbin:/usr/sbin

pidfile=/var/run/syslogd.pid
binpath=/sbin/syslogd

test -x $binpath || exit 0
. /lib/lsb/init-functions

# Options for start/restart the daemons
#   For remote UDP logging use SYSLOGD="-r"
#
SYSLOGD="-u syslog -a /var/lib/named/dev/log"

create_xconsole()
{
    if [ ! -e /dev/xconsole ] said:**
> 
    then
        return 1
    fi

    pid=`cat $pidfile`

    # No pid, probably no daemon present
    #
    if [ -z "$pid" ]
    then
        return 1
    fi

    if [ ! -d /proc/$pid ]
    then
        return 1
    fi

    cmd=`cat /proc/$pid/cmdline | tr "\000" "\n"|head -n 1`

    # No syslogd?
    #
    if [ "$cmd" != "$binpath" ]
    then
        return 1
    fi

    return 0
}

case "$1" in
  start)
    log_begin_msg "Starting system log daemon..."
    create_xconsole
    start-stop-daemon --start --quiet --exec $binpath -- $SYSLOGD
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping system log daemon..."
    start-stop-daemon --stop --quiet --oknodo --exec $binpath --pidfile $pidfile
    log_end_msg $?
    ;;
  restart|force-reload|reload-or-restart|reload)
    log_begin_msg "Restarting system log daemon..."
    start-stop-daemon --stop --quiet --exec $binpath --pidfile $pidfile
    sleep 1
    start-stop-daemon --start --quiet --exec $binpath -- $SYSLOGD
    log_end_msg $?
    ;;
  *)
    log_success_msg "Usage: /etc/init.d/sysklogd {start|stop|reload|restart|force-reload|reload-or-restart}"
    exit 1
esac

exit 0

```


Restart the logging daemon:

```
/etc/init.d/sysklogd restart
```

Start up BIND, and check /var/log/syslog for any errors:

```
/etc/init.d/bind9 start

```

---

