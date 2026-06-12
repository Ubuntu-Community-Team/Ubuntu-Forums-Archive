---
title: "ebox"
date: 2010-05-11
forum: Server Platforms
---

### Post by rzbierski on 2010-05-11
hello,
I tried to configure Firewall to block one PC to access to the Internet. 

I have two interface:
eth0-LAN (192.168.1.0/24)
eth1-WAN (83.x.x.x/29) this interface has External(WAN) checked 

I have one PC 192.168.1.101 and I would like to block the access to WWW, FTP for this PC.

I created these rules:
Filtering rules from internal networks to eBox : DENY;SRC:192.168.1.101/32;http
Filtering rules for internal networks: DENY; SRC:192.168.1.101/32;  DST:ANY  ;  http

And there is no other rule. And on this PC, internet Access works but shoudn't. What I'm doing wrong ??

---

