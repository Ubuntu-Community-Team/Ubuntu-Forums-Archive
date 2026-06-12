---
title: "Firefox must run before apt-get can download from repos"
date: 2014-06-23
forum: Ubuntu Development Version
---

### Post by jimmy-frydkaer on 2014-06-23
The Computer:

MSI MegaBook M670:

AMD Mobile Sempron 3400+
2 Gig RAM (DDR1)
nVidia GeForce Go 6100 (512 MB RAM)
Hitachi HTS 54161 - 160 GB hdd

Laptop is installed with Ubuntu GNOME 14.10 pre-alpha, with kernel 3.15.0.6 generic.

My laptop runs well overall speaking. But I have encountered this problem that if I, via wireless connection to public hotspot behaves strange.

As a GNOME extension I have the "Drop-Down-Terminal" installed which make system work a lot easier. 

If I am connected to the internet via my wifi network card, on board, and have nothing else open that the DDT to do an upgrade, as I do several times a day, I can no longer access the I-net through the drop-down-terminal, it does not connect. Same issue with a terminal window invoked by ctrl+alt+t.

Neither of the two terminals are able to connect and upgrade the system. And NOW I get confused.

IF I let Firefox run in the background while working with the terminal those problems does not exist. Only if I close FF I am unable to use the best tool of all to upgrade: The CLI

Does anyone of you experience the same flaw?

---

### Post by tgalati4 on 2014-06-23
If you are running on battery, then it is possible that the wifi card is going to sleep to save battery.  Does the behavior change with AC power?  I would check the BIOS for power-saving settings that relate to wireless and turn them off and see if the behavior changes.

Using public wifi is hard to troubleshoot, since you don't control the router.  It's possible that there is Quality-of-Service (QoS) filters that allow http traffic (so browsers work), but limit any other TCP/IP traffic (like wget and apt-get).

Ping the package repository to see what the connection time is:

> tgalati4@Mint14-Extensa ~ $ ping packages.ubuntu.com
PING packages.ubuntu.com (91.189.94.203) 56(84) bytes of data.
64 bytes from jubany.canonical.com (91.189.94.203): icmp_req=1 ttl=41 time=189 ms
64 bytes from jubany.canonical.com (91.189.94.203): icmp_req=2 ttl=41 time=189 ms
64 bytes from jubany.canonical.com (91.189.94.203): icmp_req=3 ttl=41 time=189 ms
64 bytes from jubany.canonical.com (91.189.94.203): icmp_req=4 ttl=41 time=191 ms
64 bytes from jubany.canonical.com (91.189.94.203): icmp_req=5 ttl=41 time=191 ms
^C
--- packages.ubuntu.com ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5004ms
rtt min/avg/max/mdev = 189.148/190.296/191.812/1.204 ms


---

