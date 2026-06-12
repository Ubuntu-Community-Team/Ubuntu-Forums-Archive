---
title: "connecting two servers acroos wifi router"
date: 2020-09-18
forum: Virtualisation
---

### Post by wall-545 on 2020-09-18
[COLOR=#333333][FONT=&quot]Hi, i have two laptops each one with ubuntu 16, connected to a router by wifi.
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]First L1[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]gateway: 192.168.190.2[/FONT][/COLOR][COLOR=#333333][FONT=&quot]**CODE: [SELECT ALL]("https://forums.centos.org/viewtopic.php?f=50&t=75727#")**
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    100    0        0 ens33
192.168.190.0   0.0.0.0         255.255.255.0   U     100    0        0 ens33
Second L2
gateway: 192.168.5.2
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
default         gateway         0.0.0.0           UG    100    0        0 ens33
192.168.5.0     0.0.0.0          255.255.255.0    U      100    0       0 ens33
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]no firewall in boith linux[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]both have ping to router. 192.168.1.1, but cannot ping from L1 to L2 or L2 to L1, the question is, which  route is needed to add, or is necessary to create a bridge or vlan by Network Connections or what, thanks[/FONT][/COLOR]

---

### Post by TheFu on 2020-09-18
First, put them on the same subnet.
Also, if they are servers, your life will be much easier if both systems have static IPs.

The same subnet part probably requires a change inside the router settings.

---

### Post by wall-545 on 2020-09-18
i  set both in same subnet 192.168.190.x, but the same behaviour, no pings between L1 and L2

---

### Post by wall-545 on 2020-09-18
I have  to say that both  linux are vmware VM's

---

### Post by TheFu on 2020-09-18
> **wall-545 said:**
> I have  to say that both  linux are vmware VM's

That's a pretty important detail.

a) VMs don't use wifi unless you did something really hard.  They use virtual networking provided by the hostOS.
b) Ensure both systems are set to "bridged" networking, not NAT, not host-only, but "bridged".

---

### Post by QIII on 2020-09-18
Moved to Virtualisation

---

### Post by wall-545 on 2020-09-18
yes you are right with bridged, both linux are now in sublan 192.168.1.x, it works for me, thanks :D

---

