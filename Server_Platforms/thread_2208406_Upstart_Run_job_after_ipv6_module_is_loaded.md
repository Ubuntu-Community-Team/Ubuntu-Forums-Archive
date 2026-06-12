---
title: "Upstart: Run job after ipv6 module is loaded"
date: 2014-02-28
forum: Server Platforms
---

### Post by _saiko on 2014-02-28
Hi,	

I'm trying to start an upstart job after making sure networking interfaces are up, actually after ipv6 module is started.

This is what I have now:

```
start on started network-interface INTERFACE=eth0
stop on runlevel [!2345]

pre-start script
    test -x /usr/sbin/dibbler-client || { stop; exit 0; }
    test -c /dev/null || { stop; exit 0; }

end script

exec /usr/sbin/dibbler-client start 2>&1 > /dev/null
```

The problem is that dibbler is obviously started too soon since i'm getting > Client Critical Interface eth0/2 is down or doesn't have any link-local address.
Basically ipv6 and/or interface isn't started before dibbler is started.
Is there a simple way of solving this with events or i'd have to do it in the pre-start ? I'm using only /etc/networking/interfaces and the networking script for configuration. So no network manager.
I tried different combinations for "start on" but no reall success.

Could I just use sleep in the pre-start script since few seconds seem to do the trick?

I'm using server build 12.04 LTS.

---

### Post by ian-weisser on 2014-02-28
> **_saiko said:**
> start on started network-interface INTERFACE=eth0

I use:
```
start on net-device-up IFACE=eth0
```

---

### Post by _saiko on 2014-02-28
That was one of the first "start on" lines I tried.

There, I edited the first post to clarify things a bit.

---

### Post by _saiko on 2014-02-28
The main problem was that the ipv6 wasn't started even though the interface was up.

Doing some browsing there was a suggestion to start the ipv6 module right during boot by editing the /etc/modules .

Another solution is supposedly to enable the inactive-mode in the dibbler configuration /etc/dibbler/client.conf

I wanted to do it purely in upstart script so here's the .conf file that I tested and seems to be working:

```
# dibbler-client
#
# The dibbler dhcpv6 client

description     "dibbler-client"

start on (started network-interface
          or started network-manager
          or started networking)
stop on runlevel [!2345]

pre-start script
    test -x /usr/sbin/dibbler-client || { stop; exit 0; }
    test -c /dev/null || { stop; exit 0; }

    TIMEOUT=50 #5 second timeout - eatch iteration sleeps for 1/10th of a second
    LOG_FILE=/tmp/dibbler_upstart.log

    until [ $TIMEOUT -eq 0 ]; do
        if ip addr show dev eth0 | grep -e 'inet6.*link.$'; then
                echo "Detected inet6 link-local, exiting" >> $LOG_FILE
                ip addr show dev eth0 >> $LOG_FILE
                exit 0;
        fi
        TIMEOUT=$((TIMEOUT-1))
        sleep .1
    done

    echo "Timeout waiting for IP address" >> $LOG_FILE
    exit 1;

end script

exec /usr/sbin/dibbler-client start 2>&1 > /dev/null
```

If someone knows how to detect ipv6 status with events that would be a cleaner solution.

---

