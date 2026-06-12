---
title: "(64 bit) LAN DNS, web servers?"
date: 2012-06-21
forum: Server Platforms
---

### Post by kin37ik on 2012-06-21
g'day, ive been scouring the net looking for some clearer tutorials on setting up DNS servers correctly in ubuntu server 11.10 on a LAN which is something i still havent gotten my head around, ive got 5 boxes laying around and i thought id like to experiment with them and what i realistically want to experiment with is running an intranet, so i want to try and go this route:

run one as a Root Hint type server
run two as a TLD (top level domain) 
and then have one webhost box under one TLD, and then the other webhost box  under the other TLD

might seem a strange way to go, especially if i want to run it on a Local Network only, but i really want to learn about this kind of thing, can anyone impart some knowledge and insight?

---

### Post by darkod on 2012-06-21
This is the official documentation:
[https://help.ubuntu.com/11.10/serverguide/dns.html](https://help.ubuntu.com/11.10/serverguide/dns.html)

Here you have DNS among other things (it's quite old, for version 8.10 but should still apply):
[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

If you google for more tutorials I am sure you will find loads.

---

