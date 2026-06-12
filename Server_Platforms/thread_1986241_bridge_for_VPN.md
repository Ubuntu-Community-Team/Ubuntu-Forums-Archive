---
title: "bridge for VPN"
date: 2012-05-24
forum: Server Platforms
---

### Post by minisaurus on 2012-05-24
Hi all,
I'm trying to install a bridge on an Ubuntu server (10.04) for OpenVPN.  I've followed ubuntu help guidance but confess I don't really have a  clue what I'm doing. I've added br0 to /etc/network/interfaces as guided  but suspect I've messed it up.

The ubunut server is behind a router, the router is 192.168.1.1, the  ubuntu server 192.168.1.10 and I made the bridge 192.168.1.11, but the  last was a guess. HEre is /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

# Bridge - added by PD 2012-05-23 - br0 address should be different to eth0?
auto br0
iface br0 inet static
    address 192.168.1.11
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    bridge_ports eth0
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

any help appreciated 

Thanks in advance 

Mini

---

