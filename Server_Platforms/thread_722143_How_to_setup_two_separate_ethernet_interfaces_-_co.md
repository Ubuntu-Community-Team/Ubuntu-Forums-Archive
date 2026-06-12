---
title: "How to setup two separate ethernet interfaces - correctly"
date: 2008-03-12
forum: Server Platforms
---

### Post by frankiet on 2008-03-12
I have an Ubuntu 7.10 server that has two nics, one that is connected to a network that has a DHCP service (eth1), the other connected to a separate network with no DHCP service (eth0).  This server will be used for VMWare Server: eth1 will be used for config/maintenance whereas eth0 will be used for VM virtual nics.

How do I properly configure eth0 with a static IP?  Do I need to add an entry to resolve.conf in order for the two nics to work correctly?

---

### Post by SpaceTeddy on 2008-03-12
all configration for the network interfaces are done in /etc/network/interfaces - in your case you would want a setup that would look something like this added/replaced:

> auto eth0 eth1

iface eth0 inet static[INDENT]address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.0
network 192.168.0.0
[/INDENT]
iface eth1 inet dhcp

this will try to obtain a dhcp lease for eth1 and set the static information on eth0. The first line makes sure that the devices are configured during boot-time (remove the empty line just before the address part - this editor won't let me do it)

Anything that is not supplied by the dhcp (by your statement, i think DNS and gateway are supplied) needs to be set accordingly... just thought i'd mention that

---

