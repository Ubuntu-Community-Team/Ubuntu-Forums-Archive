---
title: "Setting Static IP address"
date: 2010-05-17
forum: Server Platforms
---

### Post by irv on 2010-05-17
I just upgraded to 10.04 and I want to set the static ip address but I can't find where to do it. Can some one help?
Thanks.

---

### Post by Speonge_Bob on 2010-05-17
Maybe this will help:

[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address. Edit /etc/network/interfaces and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100)

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.100
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1

---

### Post by irv on 2010-05-18
Thanks for the help
This solved the problem

---

