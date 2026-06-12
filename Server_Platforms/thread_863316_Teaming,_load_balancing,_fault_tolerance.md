---
title: "Teaming, load balancing, fault tolerance?"
date: 2008-07-18
forum: Server Platforms
---

### Post by FTBPrimeEvil on 2008-07-18
can ubuntu server do teaming, load balancing, fault tolerance?

I have a new HP Proliant ML350 G2 with nothing but Ubuntu Server installed, i want to take advantage of dual NIC's.

This is the last issue to solve with this server!

Thank YOU!

---

### Post by RealPSL on 2008-07-20
You are looking to use NIC teaming. Take a look at the links below and see if they are helpful.  Just remember that your network adapter may not necessarily be e100 (Intel).

[http://www.howtoforge.com/nic_bonding]("http://www.howtoforge.com/nic_bonding")

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5411141]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5411141")

---

### Post by windependence on 2008-07-20
More that mat help you. There are all kinds of ways to do this. :)

[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

-Tim

---

### Post by Kromey on 2008-07-20
If you're looking to use DHCP for this server and you use bonding to team your NICs, you may want to check out my post here:
[http://ubuntuforums.org/showthread.php?t=864657](http://ubuntuforums.org/showthread.php?t=864657)

Simply setting up the bonding interface to use DHCP doesn't work, and of course that's only mentioned as an after-thought with no solution offered in countless otherwise well-written how-tos. :KS

---

### Post by sara.m on 2009-11-06
[COLOR=black][FONT=Verdana]HI,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have a Question.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Is it possible that we have  reliability more than availability in a system? How? If yes, please say some example.[/FONT][/COLOR]

---

### Post by skotos on 2009-11-08
@ realPSL, windependence, Kromey: thank you guys!

I have followed the UbuntuBonding link and worked immediately in Karmic.
To avoid mess up I simply uninstalled the NetWork Manager, its gnome applet, followed the instructions and restarted: IT WORKED. It was a truly 5 minutes time activity.

---

