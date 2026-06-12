---
title: "Need help setting up Ubuntu Hardy Heron Server"
date: 2009-03-06
forum: Server Platforms
---

### Post by garrett1415 on 2009-03-06
I'm in the middle of setting up an Ubuntu Hardy Heron Server, using these instructions: [http://www.howtoforge.com/perfect-server](http://www.howtoforge.com/perfect-server)...

I'm on page 3, and I'm stuck configuring the network.

Heres what I need to fill out:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address Done
netmask I think I have this, it is the Subnet Mask?
network ?
broadcast ?
gateway Done

I need to find the network and broadcast? Where can I find these? And this the netmask the same as the subnet mask?

Thanks so much!

---

### Post by benblout on 2009-03-07
First, I am not an expert in Servers.  But I would have some hesitations about that guide - the first thing I read on page three was a suggestion to give root a passwd, so you can use su.  My understanding is that using sudo exclusively gives you much better security.

Secondly, if you don't know otherwise (because of how you have configured your network) the entries shown in the example should work, if you are using the common 192.168.0.* network configuration.

---

