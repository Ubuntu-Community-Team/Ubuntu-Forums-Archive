---
title: "Need help setting up a wireless access point"
date: 2007-11-22
forum: Server Platforms
---

### Post by dashnak on 2007-11-22
Hello, I'm trying to set up a PC running 7.10 server as an access point.
It has two interfaces, one wired, which gets internet from my router, and one wireless which, hopefully, will spit out some internet to other boxes.
My wireless card is a PCI NETGEAR WG311 V2 with an ACX chipset.
I compiled the latest drivers from [http://[SIZE=-1]](http://[SIZE=-1])**acx**100.sourceforge.net/
My card is recognized just fine with ifconfig, I can even surf the net with it.
I've configured my /etc/network/interfaces, so that every interface is down on boot. And then, once I log in, I run this script:

[/SIZE]```

#!/bin/sh

ifconfig eth0 down
ifconfig wlan0 down
ifconfig wlan0 0.0.0.0 up
ifconfig eth0 0.0.0.0 up
iwconfig wlan0 mode master
iwconfig wlan0 essid "ALITA" channel 6
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0
dhclient br0
```

And create a bridge.
Once done, I can see the recently created network "ALITA", can even associate to it, but have no exit to the internet when I connect to it.
I am aware that there's no DHCP in this access point, and accordingly I configure everything manually, but it is still not working.
Any ideas?

---

