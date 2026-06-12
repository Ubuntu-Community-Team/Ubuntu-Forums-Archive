---
title: "Some questions regarding using my ubuntu box as a router/gateway"
date: 2008-05-01
forum: Server Platforms
---

### Post by calypso612 on 2008-05-01
Currently I'm installing and configuring a new linux box for use as a router/firewall/vpn. Currently I'm in the beginning stages but moving along quickly thanks to the many HOWTO's on the subject.

I'm running into some problems...questions more regarding bind9 DNS service. More specifically. If I want the computers on my network to be able to get the DNS from the ISP, do I need bind? If so how do I configure it to do so. If it doesn't the same question regarding configuration.

On a side note the only thing this computer does is act as the router/firewall and vpn. So I'm purposefully keeping it a minimalistic install.

---

### Post by koenn on 2008-05-01
> **calypso612 said:**
> If I want the computers on my network to be able to get the DNS from the ISP, do I need bind?.
No.
The only reasons you'd need bind would be
1- you have an extensive private local network and you want to use hostnames in stead of ip addresses - your ISP's DNS can't do that because it doesn't know the names of computers on your private network

2- You don't want to allow your netwerk hosts to connect to the internet for dns etc, so you use a local DNS server/cache/... to handle that. Simplifies firewall configuration somewhat but forces you to provide DNS (not necessarily bind. Something like dnsmasq would do in this case)

---

