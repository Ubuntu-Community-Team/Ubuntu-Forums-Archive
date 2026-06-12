---
title: "KVM Bridging with a Bonded Network Interface"
date: 2011-10-31
forum: Server Platforms
---

### Post by jacob.air on 2011-10-31
Im trying to setup a KVM virtual machine with a bridge using a bonded network interface. The goal is to have the host server and the virtual server running on the KVM both accessible from the LAN through the 4 port bond0. On the host server all is fine when the network configuration doesn't include the br0 (The server can be connected to from all network subnets and can also see all network subnets). However, when br0 is enabled and working the server cannot be found from anywhere except 192.168.1.0. The virtual machine can also be connected to through the bridge from that LAN, but not any other subnets. It seems that br0 works over the bond, but lacks the ability to negotiate ip's outside of that subnet. Disable br0 again and the server can be connected to from all other subnets fine, but the virtual machine is obviously inaccessible.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Bonded network interface
auto bond0
iface bond0 inet static

        address 192.168.1.61
        gateway 192.168.1.1
        broadcast 192.168.1.255
        netmask 255.255.255.0
        bond-slaves eth0 eth1 eth2 eth3
        bond_mode 5
        bond-miimon 100

# AIRUV1 bridge interface
auto br0
iface br0 inet static

       address 192.168.1.62
       network 192.168.1.0
       gateway 192.168.1.1
       netmask 255.255.255.0
       broadcast 192.168.1.255
       bridge_ports bond0
       bridge_hello 2
       bridge_stp off
       bridge_fd 9
       bridge_maxwait 12

```

---

### Post by ekko_ on 2011-11-01
Try this and see if it works for you

```
auto bond0
iface bond0 inet manual
       [INDENT]slaves eth0 eth1 eth2 eth3
       bond-mode 5
       bond-miimon 100
[/INDENT]
auto br0
iface br0 inet static

       [INDENT]address 192.168.1.62
       network 192.168.1.0
       gateway 192.168.1.1
       netmask 255.255.255.0
       broadcast 192.168.1.255
       bridge_ports bond0
       bridge_hello 2
       bridge_stp off
       bridge_fd 9
       bridge_maxwait 12[/INDENT]
```

---

