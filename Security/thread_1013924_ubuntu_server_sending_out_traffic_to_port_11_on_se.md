---
title: "ubuntu server sending out traffic to port 11 on selected machines"
date: 2008-12-17
forum: Security
---

### Post by davidshere on 2008-12-17
We recently moved a server from outside our firewall to inside.  Our firewall logs now show this box sending traffic to a destination port 11 on two internal devices.  One is a switch and the other is another server.  Here is a sample from the firewall log:

[B]
12/17/2008 00:27:23.160 - Notice - Network Access - 	UDP packet dropped - 	***.***.***.***, 34257, X2, source.server.name - 	***.***.***.***, 53, X0, destination.server.name - 	UDP DNS (Name Service) UDP 11 (DMZ->LAN)
[/B]

My question is: How can I find out what application or process on the source server is sending this traffic?

---

### Post by Kinstonian on 2008-12-17
I don't think that's UDP port 11, that looks like UDP DNS traffic.  The 11 is actually UDP's protocol number.

UDP = 11
ICMP = 1
TCP = 6

---

### Post by davidshere on 2008-12-17
I was misreading that message -- "11" is the rule number on the firewall that blocked the traffic.   There is no problem here.

---

