---
title: "Ethernet Bonding Problems"
date: 2013-08-02
forum: Server Platforms
---

### Post by Jacob_Heutlinger on 2013-08-02
I am relatively new to Ubuntu Server but I am using a Samba server with 2 Ethernet ports currently bonded by balance-alb.  I am trying to figure out what method of bonding to use for the fastest speeds in my case.  Thank you.
This is my /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
bond-master bond0


#eth1
auto eth1
iface eth1 inet dhcp
bond-master bond0


#bonding
auto bond0
iface bond0 inet static
address 192.168.1.128
netmask 255.255.255.0
gateway 192.168.1.1
bond-mode balance-alb
bond-miimon 100
bond-slaves eth0 eth1

---

### Post by newbie-user on 2013-08-02
I'd go with link aggregation if you have a switch that supports it. If not, then you're probably already set up as good as can be with alb.

---

