---
title: "No network device under XP as guest on virtualbox"
date: 2008-11-20
forum: Virtualisation
---

### Post by phazer on 2008-11-20
I run 8.10 and want to run TinyXP to get Outlook to run to connect to the company exchange server. Xp runs perfectly, except no network device.

I have tried the following :
phazer@black:~/Downloads$ sudo tunctl -t tap1 -u phazer
phazer@black:~/Downloads$ sudo tunctl -t tap1 -u phazer
Set 'tap1' persistent and owned by uid 1000
phazer@black:~/Downloads$ sudo brctl addbr br0
phazer@black:~/Downloads$ sudo ifconfig eth0 0.0.0.0 promisc
phazer@black:~/Downloads$ sudo brctl addif br0 eth0
phazer@black:~/Downloads$ sudo dhclient br0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/br0/00:21:70:c4:0a:60
Sending on   LPF/br0/00:21:70:c4:0a:60
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 10.1.71.56 from 10.1.71.1
DHCPREQUEST of 10.1.71.56 on br0 to 255.255.255.255 port 67
DHCPACK of 10.1.71.56 from 10.1.71.1
bound to 10.1.71.56 -- renewal in 39962 seconds.
phazer@black:~/Downloads$ sudo brctl addif br0 tap1
phazer@black:~/Downloads$ sudo ifconfig tap1 up
phazer@black:~/Downloads$ sudo chmod 0666 /dev/net/tun

and then setting host device to tap1 under network for the guest xp box, but still nothing.

Anyone have ANY idea?

---

