---
title: "How do i use a vyatta VM to manage my LAN/WAN connections?"
date: 2010-06-19
forum: Virtualisation
---

### Post by myiknow on 2010-06-19
I have a simple problem that is difficult to explain, so please bear with me. I am trying to use a Vyatta VM router to manage my LAN. I have connectivity thoughout my lan but I cannot get outside of my LAN from the VM. I have have a linux box running ubuntu 8.04 + vmware server 2.0.2 + vyatta VC6. eth1 on the box gets a public IP from my ISP (we'll say 1.1.1.2 for demonstration). 
 
eth1 has a VLAN interface eth1.2 with private IP 192.168.1.2/24. 
I have a few more NICs that are bridged to interface br0 with IP 192.168.2.2/24. 
 
Ubuntu eth1 (1.1.1.2) <-- WAN
Ubuntu eth1.2 (192.168.1.2/24) <-- LAN 1
Ubunru br0 (192.168.2.2/24) <-- LAN 2
 
Vyatta eth0 (192.168.1.1/24) is bridged to eth1.2 <-- LAN 1
Vyatta eth1 (192.168.2.1/24) is bridged to br0 <-- LAN 2
 
The routes on both the linux box and vyatta appear to be setup correctly but I am unable to ping from the Vyatta VM to the internet (lets say google [74.125.45.105]) or to my ISP gateway address 1.1.1.1 I can however ping from the Vyatta VM to the linux box eth1 1.1.1.2 which is a "public" IP. I thought adding a static route for 0.0.0.0/0 next-hop 1.1.1.2 would do it but still no cookie. Anyone know what the problem is??
 
Text Graphic :)
192.168.1.1---> 192.168.1.2---> 1.1.1.2 --->X WWW
Vyatta VM Ubuntu Ubuntu
eth0 eth1.2 eth1

---

