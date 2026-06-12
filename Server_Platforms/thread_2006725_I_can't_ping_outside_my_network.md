---
title: "I can't ping outside my network"
date: 2012-06-19
forum: Server Platforms
---

### Post by abrolho on 2012-06-19
Hi people,

I have a Ubuntu Server 10.04 LTS with Squid + Iptables sharing a internet link for 100 computers.

The problem is i can acess the internet websites but i cant ping them. 
I can ping the internal ip's but not external (outside my network).

What can i do to fix that?

Thanks!

---

### Post by LHammonds on 2012-06-19
I would venture to guess your firewall is blocking it.

To allow pings to go through your firewall, open up outbound ICMP.

LHammonds

---

### Post by arrrghhh on 2012-06-19
Assuming you have allowed ICMP out, not all sites will let ICMP in.

A good test is 8.8.8.8 ;).

---

