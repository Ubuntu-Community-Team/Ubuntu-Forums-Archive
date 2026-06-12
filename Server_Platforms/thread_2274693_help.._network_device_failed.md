---
title: "help.. network device failed"
date: 2015-04-21
forum: Server Platforms
---

### Post by amerinde on 2015-04-21
hello.. i ran into a problem here.. on boot up i get

configure network device [fail] and 
configure virtual network device [fail]

ifconfig only shows. lo but no eth0

actually this started yesterday, when i lost ability to WOL

How can i reset

---

### Post by nerdtron on 2015-04-21
probably a typo in your /etc/network/interfaces file. What else did you changed before this happened?
What happens when you:

sudo service networking restart

or

sudo ifup eth0

---

### Post by amerinde on 2015-04-24
> **nerdtron said:**
> probably a typo in your /etc/network/interfaces file. What else did you changed before this happened?
What happens when you:

sudo service networking restart

or

sudo ifup eth0

ok.. i am back, sorry took so long, was away for work.. But, 

this is a direct cp of /etc/network/interface as .txt to a USB

.# This file describes the network interfaces available on your system
..# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
up ethtool -s eth0 wol g

# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto

I used many webpages to help me, (so I thought)

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://wiki.ubuntuusers.de/Wake_on_LAN](http://wiki.ubuntuusers.de/Wake_on_LAN)  (in german)

I believe in that order, yes, i ran the script from the third and made the wakeonlanconfig

when i run 

/$sudo service networking restart
stop: Unknown instance:
start: Jpb failed to start

/$sudo ifup eth0
/etc/network/interfaces:1: misplaced option
ifup: couldn´t read interfaces file "/etc/network/interfaces" 


thanks for any help someone anyone can give me

---

