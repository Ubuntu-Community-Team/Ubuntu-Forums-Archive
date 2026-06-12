---
title: "Help setting up promiscuous mode"
date: 2009-07-28
forum: Security
---

### Post by TuckLive on 2009-07-28
I'm finishing up my Snort install, but I need to know how to setup eth1 without an IP address.  I currently have it running in DHCP.  How can I do this?  Here's my current interfaces file:

```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
      address   192.168.1.100
      netmask   255.255.255.0
      network   192.168.1.0
      broadcast 192.168.1.255
      gateway   192.168.1.1

auto eth1
iface eth1 inet dhcp

```

---

### Post by TuckLive on 2009-07-29
Found my answer.

```
auto eth1
 iface eth1 inet manual
       up ifconfig $IFACE 0.0.0.0 up
       up ip link set $IFACE promisc on
       down ip link set $IFACE promisc off
       down ifconfig $IFACE down

```

---

