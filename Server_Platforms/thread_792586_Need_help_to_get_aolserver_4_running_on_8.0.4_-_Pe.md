---
title: "Need help to get aolserver 4 running on 8.0.4 - Permission denied"
date: 2008-05-13
forum: Server Platforms
---

### Post by nexxus07 on 2008-05-13
I wonder whether anyone succeeded in configuring aolserver4 to listen on an IP address different from 127.0.0.1. I need it to install a tcl application and once I change the IP Address in the config file I get a "permission denied". It works fine as long as it listens on lo 127.0.0.1:80

from my etc/aolserver5/aolserver.tcl
```
###
#
#    GLOBAL VARIABLES
#

set httpport 80
set httpsport   443
set controlport 9999

set hostname localhost
# set address 127.0.0.1
[COLOR="Red"]set address 192.168.2.21[/COLOR]

set servername main
set serverdesc "AOLServer Site"
set package    aolserver4

```

last couple of lines from the aolserver log file:
```
[13/May/2008:02:36:50][4937.3083634352][-main-] Notice: nsmain: security info: uid=33, euid=33, gid=33, egid=33
[13/May/2008:02:36:50][4937.3074665360][-sched-] Notice: sched: starting
[13/May/2008:02:36:50][4937.3083634352][-main-] Notice: driver: starting: nssock
[13/May/2008:02:36:50][4937.3074493328][-nssock:driver-] Notice: starting
[13/May/2008:02:36:50][4937.3074493328][-nssock:driver-] [COLOR="Red"]Error: nssock: failed to listen on 192.168.2.21:80: Permission denied[/COLOR]
[13/May/2008:02:36:50][4937.3074493328][-nssock:driver-] Notice: exiting
[13/May/2008:02:36:50][4937.3083634352][-main-] Fatal: could not start drivers

```

and my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:30:13:e7  
          inet addr:192.168.2.21  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe30:13e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1446340 (1.3 MB)  TX bytes:487735 (476.3 KB)
          Interrupt:11 Base address:0xc020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:446307 (435.8 KB)  TX bytes:446307 (435.8 KB)


```

Unfortunately documentation on aolserver on ubuntu is somewhat rare. I would appreciate any pointers or your experience with aolserver4.


Thanks in advance,
Thomas

---

### Post by Cook2 on 2008-05-13
/etc/init.d/aolserver4
ADDRESS=192.168.2.21

---

### Post by nexxus07 on 2008-05-13
That's it!! Thank you so much.  I had to add the port as well but now all seems to be working. 

<Speculation start> I suspect the IP and Port are passed to nsd (aolserver) by init under root privileges which alles nsd to bind to this address. If it is only in the configuration file nsd tries to bind itself as www-data which results in the error. <Speculation end>

As a reference my first lines in /etc/init.d/aolserver

```

#!/bin/sh
#
# Start the AOLServer HTTP server.
#
# Copyright (C) 2003-2007 Francesco P. Lovergine <frankie@debian.org>
#

NAME=aolserver4
USER=www-data
GROUP=www-data
[COLOR="Red"]ADDRESS=192.168.2.21
PORT=80[/COLOR]
PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/sbin/aolserver4-nsd
PIDFILE=/var/run/aolserver4/$NAME.pid
CONF=/etc/aolserver4/aolserver4.tcl


```

---

