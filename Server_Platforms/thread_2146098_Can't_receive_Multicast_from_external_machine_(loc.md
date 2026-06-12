---
title: "Can't receive Multicast from external machine (local works) 12.10 Server"
date: 2013-05-17
forum: Server Platforms
---

### Post by oxoocoffee on 2013-05-17
I have small test app for sending and receiving multicast traffic. This app (my source) work fine on CentOS, Mac Lion an Windows. But on Ubuntu Server it only works when sending and receiving on the same box.
This test server that I did setup is multi home configuration. It has p4p1 and p1p1. The later one was added after initial server installation.
When I try to send traffic from external machine connected to same router as p1p1 interface (that I am bound to on Ubuntu) I can't get multicast traffic. But in this scenario I am running tcpdump as well on p1p1 and I can see mcast coming from external machine. But my test app does not receive it. Is there some filtering going on?
This installation is very simple (default installation). No SELinux installed, iptables are off, AppArmor configs are unchanged. I do not see any errors or messages in dmsg, syslog or audit logs.

I did configured /etc/network/interfaces with routing info

# The loopback network interface
auto lo
iface lo inet loopback

# Internet Interface
auto p4p1
iface p4p1 inet dhcp

#Multicast Interface
auto p1p1
iface p1p1 inet dhcp
    up route add -net 10.155.70.0/24 dev p1p1
    up route add -net 224.0.0.0/4 dev p1p1

Here is my routing table

Kernel IP routing table
Destination     Gateway         Genmask     Flags Metric Ref    Use Iface
default         10.200.80.1   0.0.0.0            UG    0      0        0 p4p1
10.155.70.0     *               255.255.255.0   U     0      0        0 p1p1
10.200.70.0     *               255.255.255.0   U     0      0        0 p1p1
10.200.80.0     *               255.255.255.0   U     0      0        0 p4p1
224.0.0.0        *               240.0.0.0          U     0      0        0 p1p1


#ip route
default via 10.200.80.1 dev p4p1
10.155.70.0/24 dev p1p1  scope link
10.20070.0/24 dev p1p1  proto kernel  scope link  src 10.200.70.8
10.200.80.0/24 dev p4p1  proto kernel  scope link  src 10.200.80.8
224.0.0.0/4 dev p1p1  scope link

Any one has any suggestions what is the problem here? I can provide test mcast code to send and receive mcast messages if that is needed. But this code works fine (on the same hardware with swappable CentOS)

Thanx

---

