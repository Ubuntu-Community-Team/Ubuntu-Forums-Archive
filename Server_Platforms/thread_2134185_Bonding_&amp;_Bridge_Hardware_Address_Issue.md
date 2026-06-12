---
title: "Bonding &amp; Bridge Hardware Address Issue"
date: 2013-04-10
forum: Server Platforms
---

### Post by cerealcable on 2013-04-10
So I've setup bonding with a bridge.  Everything is working fine except every once in a while on reboot the mac address changes even though I've set the hwaddress of my bond interface.  This never was a problem before I added the bridge to the setup.  Any tips or suggestions on what to do?  Seems like 25% of the time it uses one of the ethX interface hwaddresses instead.

Any suggestions would be greatly appreciated!

My /etc/network/interfaces:
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# slaves
auto eth0
iface eth0 inet manual
    bond-master bond0
auto eth1
iface eth1 inet manual
    bond-master bond0
auto eth2
iface eth2 inet manual
    bond-master bond0
auto eth3
iface eth3 inet manual
    bond-master bond0


# bond0
auto bond0
iface bond0 inet manual
    hwaddress ??:??:??:??:??:??
    bond-slaves none
    #bond-mode 802.3ad
    bond-mode active-backup
    bond-miimon 100
    bond-downdelay 200
    bond-updelay 200


# bridge
auto br0
iface br0 inet dhcp
    bridge-ports bond0
    bridge-stp off
```

---

