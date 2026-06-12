---
title: "How to configure the external  network on /etc/network/interfaces compute node"
date: 2015-01-05
forum: Server Platforms
---

### Post by lightman2 on 2015-01-05
I am trying to configure the external network parameters on the compute  node but I have a problem below is my configuration details  in the file  /etc/network/interfaces.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p1p1
iface p1p1 inet static
    address 10.10.16.232
netmask 255.255.0.0
network 10.10.0.0
broadcast 10.10.255.255
gateway 10.10.0.5


# The external network interface
auto wlan0
iface wlan0 inet manual
up ip link set dev $IFACE up
down ip link set dev $IFACE down
    
# dns-* options are implemented by the resolvconf package, 
if installed
    dns-nameservers 8.8.8.8 8.8.4.4 192.168.180.28
    
dns-search cbu.ac.zm

using the instructions from the official documentation icehouse:[http://docs.openstack.org/icehouse/install-guide/install/apt/content/basics-networking-node-compute-node.html](http://docs.openstack.org/icehouse/install-guide/install/apt/content/basics-networking-node-compute-node.html)

what is  wrong with  the above external wireless network settings? Please help as soon as possible.

---

