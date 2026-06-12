---
title: "Upgrade to Ibex broke network bonding"
date: 2009-02-20
forum: Server Platforms
---

### Post by tonymaro on 2009-02-20
I had a Hardy server set up with network bonding - bonding the two gigabit ethernet ports into a single virtual bond0 device.

I just upgraded to ibex, and this seems to be broken... the bond0 device exists, and has an IP address (static) assigned to it, but it wouldn't send or receive any traffic.

I temporarily commented out the bonding setup in interfaces, and am running off of eth0 solely.

Is there some change in Ibex that makes this not work properly anymore?

Grepped for "bond" in syslog:
```
Feb 20 00:36:08 alexandria kernel: [   12.959331] bonding: In ALB mode you might experience client disconnections upon reconnection of a link if the bonding module updelay parameter (0 msec) is incompatible with the forwarding delay time of the switch
Feb 20 00:36:08 alexandria kernel: [   12.959336] bonding: MII link monitoring set to 100 ms
Feb 20 00:36:08 alexandria kernel: [   13.056602] bonding: bond0: enslaving eth0 as an active interface with an up link.
Feb 20 00:36:08 alexandria kernel: [   13.086589] bonding: bond0: enslaving eth1 as an active interface with an up link.
```

Here's /etc/network/interfaces:
```
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
hwaddress ether 00:03:b3:48:51:2E
post-up ifenslave bond0 eth0 eth1
```

---

### Post by songshu on 2009-02-20
is the bonding module loaded?
```

lsmod | grep bonding
```

---

