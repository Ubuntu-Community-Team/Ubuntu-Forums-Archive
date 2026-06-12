---
title: "Update bind forwarders using DNS servers from DHCP"
date: 2008-10-24
forum: Server Platforms
---

### Post by npmeyer on 2008-10-24
Hi,

I'm interested in setting up an ubuntu server box as a small router for my home network.  If possible, I'd like to set up bind as a caching nameserver on the router box.  Since I get my IP address and DNS servers through DHCP from my ISP, I would like to update my bind configuration automatically whenever my DHCP lease is renewed so that it forwards queries to the servers returned by DHCP.

Anyone know if there's a simple way to do this (preferably without rolling my own scripts?)

Thanks in advance,
Nick

---

### Post by Iowan on 2008-10-24
You mentioned caching nameserver and DHCP... check **dnsmasq**.  My router (Freesco) box has **dnsmasq**, though I'm not (currently) using it for DHCP.

---

