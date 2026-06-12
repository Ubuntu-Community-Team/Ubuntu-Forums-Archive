---
title: "Netsed, IPtables, and UBUNTU VM"
date: 2016-10-23
forum: Virtualisation
---

### Post by billycryptokid on 2016-10-23
PROBLEM: I am lacking clairity on how to properly setup a virtual machine on windows 10 host with NETSED and IPTABLES. Host is using a specific application that is sending and receiving information on TCP, I would like the outbound packets from host to be routed through the virtual machine so I can edit them on the fly with NETSED.

SETUP: Windows 10 host with UBUNTU 16.04 running in VIRTUAL BOX. Have tried NAT and Bridged.

iptables -t nat -D PREROUTING -s 1.2.3.4 -d 5.6.0.0/16 -p tcp --dport 12345 -j REDIRECT --to 10101 

I have tried the above code plugging in my IP's, and keeping port 80 for both source and destination.

---

### Post by howefield on 2016-10-24
Thread moved to the "*Virtualisation*" forum.

---

