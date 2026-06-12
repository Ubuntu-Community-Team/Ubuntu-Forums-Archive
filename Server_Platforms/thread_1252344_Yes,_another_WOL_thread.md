---
title: "Yes, another WOL thread"
date: 2009-08-28
forum: Server Platforms
---

### Post by dracoix on 2009-08-28
I have been fiddling with my new server (9.0.4) for two days just to get the wake-on-lan working. I have read almost every thread relating to solving this seeming similiar and difficult problem but nothing has worked yet.

It's running off of a MSI P6N SLI (standard) with an extra LNE100TX NIC. The mobo itself supports WOL by magic packet. I couldn't get a info readout on the LNE100TX but from the day of researching I assume that it indeed does support at least via magic.

BIOS:
ACPI is Enabled (I tried mode S1 and S3)
Resume on LAN is Enabled
Resume on PCI is Enabled

Now, the mobo LAN (defaulted eth1) still recieves magic packets when the system is shutdown. I tested it, and every time I send a magic packet to the comp over LAN or the internet itself it will blink ONCE on the NIC (saying ya I'm here, but hell if I'll boot for you.) So a connection is not an issue.

The LNE100TX (eth0) however is not active when the system is shutdown. And trying to set "ethtool -s eth0 wol g" gives an error, but another source thread made it work even with the error.

Here's my halt and wakeonlan (set as a service) init scripts: 

halt:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

NETDOWN=no

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
    if [ "$INIT_HALT" = "" ]
    then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    fi

    # See if we need to cut the power.
    if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
    then
        /etc/init.d/ups-monitor poweroff
    fi

    # Don't shut down drives if we're using RAID.
    hddown="-h"
    if grep -qs '^md.*active' /proc/mdstat
    then
        hddown=""
    fi

    # If INIT_HALT=HALT don't poweroff.
    poweroff="-p"
    if [ "$INIT_HALT" = "HALT" ]
    then
        poweroff=""
    fi

    # Make it possible to not shut down network interfaces,
    # needed to use wake-on-lan
    netdown="-i"
    if [ "$NETDOWN" = "no" ]; then
        netdown=""
    fi

    log_action_msg "Will now halt."
    halt -d -f $poweroff $hddown 
}

case "$1" in
  start)
    # No-op
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    do_stop
    ;;
  *)
    echo "Usage: $0 start|stop" >&2
    exit 3
    ;;
esac

:

```wakeonlan:
```
#! /bin/sh
#
# Ensures that Wake on Lan works
#

#PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

set -e

case "$1" in
  stop|start|restart|force-reload|reload)
        echo -n "Turn on: Wake on Magic Packet"
        /usr/sbin/ethtool -s eth0 wol g
        /usr/sbin/ethtool -s eth1 wol g
        echo
        ;;
  *)
#       N=/etc/init.d/hwtools
#       echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```And yes, the WOL magic packet sender (remotely) works and is properly formatted.

I hate leaving the server on 24/7, but if I have to I will. Not until I know for sure that WOL will never work for this machine.

I am at your bidding oh mighty gurus.

---

### Post by volkswagner on 2009-08-28
I have seen where all things tell me the machine should wake on lan, yet it refuses.  Most cases these units will wake only from standby, not an off state.  With Linux and ACPI difficulties, standby is often not an option.  You could possibly test the theory by booting your server with Ubuntu Desktop version (live CD) and see if standby works, then try to wake it from standby.

Have you tried disabling the onboard lan in the BIOS, to see if your add-on card will play nice?

---

### Post by dracoix on 2009-08-28
Turned off on-board LAN and it's WOL, but kept WOL via PCI still no-go. The NIC doesn't light up when connected and shutdown.

I don't have an ubuntu live cd to test, and downloading one will take a few hours. Anyway to initialize a true S1 standby from a command line?

---

### Post by volkswagner on 2009-08-28
I don't think you will want to open a can of worms...ACPI on your server to get sleep working.

---

### Post by dracoix on 2009-08-28
I've been in a can of worms before with linux servers many of them having to reinstall. However, this is a fairly new server setup so I'll give it a try by installing acpi-support and acpi init's.

---

