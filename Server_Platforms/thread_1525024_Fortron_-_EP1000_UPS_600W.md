---
title: "Fortron - EP1000 UPS 600W"
date: 2010-07-06
forum: Server Platforms
---

### Post by fiat500 on 2010-07-06
Hi all.

I have an UBUNTU SERVER and Forton UPS(included CD but software only  for Windows)    and they are not comunicating, i tried with USB and with RS232 but nothing.  anyone can recommend a software or any solution . thanks.

---

### Post by CannibalZerg on 2010-07-06
You need to install and configure NUT, but it isn't trivial. First of all you need to know which NUT driver should be used with your UPS. 
To figure out the ID of your UPS run **lsusb** first with detached UPS, then connect UPS to USB and run **lsusb** again. Find the line, that appears after attaching UPS and use it's ID value to run command
**lsusb -v -d XXXX:YYYY**, where XXXX:YYYY is a vendor and  product ID, and post it's result here.

---

### Post by fiat500 on 2010-07-06
it is 0665:5161
Bus 005 Device 005: ID 0665:5161

---

### Post by CannibalZerg on 2010-07-06
> **fiat500 said:**
> it is 0665:5161
Bus 005 Device 005: ID 0665:5161
OK, it's a standard USB-COM adapter (my UPS has the same ID), I hope that one of the megatek or blazer_ drivers will be suitable.

1) Install NUT
```

sudo apt-get install nut

```2) Connect UPS to COM1
3) Change permission of ttyS0 for testing purposes
```

sudo chgrp nut /dev/ttyS0

```4) Open */etc/nut/ups.conf*  and add to the end of file:
```

[fortron]
             driver = megatec #or blazer_ser
             port = /dev/ttyS0
             desc = "Fortron EP 1000"

```4) [I]/etc/nut/nut.conf
[/I]```

MODE=standalone

```5) */etc/nut/upsd.users*
```

[admin]
    password = adm_pwd
    action = SET
    instcmds = ALL
[local_mon]
    password = ups_pwd
    allowfrom = localhost
    upsmon master

```6) /etc/nut/upsmon.conf
```

MONITOR fortron@localhost 1 local_mon ups_pwd master
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h +0"
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
NOTIFYFLAG ONLINE SYSLOG
NOTIFYFLAG ONBATT SYSLOG
NOTIFYFLAG LOWBATT SYSLOG
NOTIFYFLAG FSD SYSLOG+WALL
NOTIFYFLAG COMMOK SYSLOG
NOTIFYFLAG COMMBAD SYSLOG
NOTIFYFLAG SHUTDOWN SYSLOG+WALL
NOTIFYFLAG REPLBATT SYSLOG+WALL
NOTIFYFLAG NOCOMM SYSLOG
NOTIFYFLAG NOPARENT SYSLOG
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 5

```
7) start NUT daemon: [I]sudo /etc/init.d/nut start
[/I]8.)check for errors in logs: [I]
     tail /var/log/daemons.log[/I]   
     *tail /var/log/messages*
9)ensure that /dev/ttyS0 has rw permission for group *nut*

10) Check UPS parameters status: *upsc fortron*

If you got messge "communication with UPS lost" or similar, it means that we trying to use wrong NUT-driver. Stop the daemon with */etc/init.d/nut stop* and edit */etc/nut/ups.conf  * Try to use "blazer_ser"driver instead of "megatec".

---

### Post by fiat500 on 2010-07-12
Hi .
Thanks for answer but unfortunately i got this with both driver
: Error: Connection failure: Connection refused

---

### Post by CannibalZerg on 2010-07-12
Try to connect it with USB and choose "usbhid-ups" driver.
 */etc/nut/ups.conf*  
```

[fortron]
     driver = usbhid-ups
     port = auto
     desc = "Fortron EP 1000"

```Also you can try another drivers, here the list of available NUT drivers: 
[http://www.networkupstools.org/compat/stable.html](http://www.networkupstools.org/compat/stable.html)

---

### Post by ottestad on 2010-07-15
I've just bought a similar UPS, Fortron EP 850, and am able to use the "blazer_ups"-driver in nut in Ubuntu 10.04.

Used the tutorial here: [http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/) and here: [https://keystoneit.wordpress.com/2006/09/25/network-ups-tools-nut-on-ubuntu/](https://keystoneit.wordpress.com/2006/09/25/network-ups-tools-nut-on-ubuntu/)

Hope this helps ;)

---

### Post by ivanatora on 2010-12-27
This is the best Fortron EP1000 linux thread I have found, but unfortunately the drivers can't connect. I tried all the drivers noted here, but no one of them worked. Finally I started trying one over another with upsdrvctl -D and blazer_usb was a success. I'm posting it here in case someone like me hit the wall :)

---

