---
title: "Setting up my first server..."
date: 2008-06-22
forum: Server Platforms
---

### Post by sp0nge on 2008-06-22
I want to experiment with the possibility of hosting my own websites for my businesses, and I've installed Hardy Server without issue. Now that I'm setting this up, I find myself in new territory. 

I'm following a guide that suggests editing /etc/network/interfaces to configure the network settings as follows:
```
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
```

What I'm confused with is the broadcast IP. Is this the external IP from my router? I found another thread here that suggested the network and broadcast lines are the same so I am confused. :confused:

---

### Post by tamoneya on 2008-06-22
they are not the same thing but they are related.  Typically I use a network calculator to figure out all of the IPs.  I typically use this site: [http://www.subnetmask.info/](http://www.subnetmask.info/)
Also read this wiki page: [http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)

---

### Post by PilotJLR on 2008-06-22
BTW, your broadcast and network addresses you've posted are correct.  :-)

---

