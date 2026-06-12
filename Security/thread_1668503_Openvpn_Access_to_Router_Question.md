---
title: "Openvpn Access to Router Question"
date: 2011-01-16
forum: Security
---

### Post by ozz0 on 2011-01-16
After I installed openvpn. I can openvpn and tunnel to my home network and access my router from machine A by going to the browser: 

192.168.0.1

However, I install the same openvpn client on machine B, I can access the local machines on my home network but I can't access my home router 192.168.0.1. Instead, that address direct me to the local network's router, but not my home router. Seems the tunneling doesn't work for the router. What can be the reason?

I have my interfaces file as below:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo br0
iface lo inet loopback

# Bridge for openvpn
iface br0 inet static
  address 192.168.0.104
  netmask 255.255.255.0
  gateway 192.168.0.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down

---

