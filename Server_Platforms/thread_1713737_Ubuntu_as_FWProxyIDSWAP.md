---
title: "Ubuntu as FW/Proxy/IDS/WAP"
date: 2011-03-24
forum: Server Platforms
---

### Post by yeleek on 2011-03-24
Hi,

I want to build a firewall/proxy/ids/wireless access point.  I know I could use Astaro/ClearOS/Pfsense for this (except possibly the wireless part).  I figure I'll learn far more if I do it myself manually rather than relying on a prepared distro.

Has anyone ever done anything similar with Ubuntu or Debian?  If so care to provide some insight please?

Thanks

---

### Post by Frizianz on 2011-03-25
If you have  a router with built in wireless you can just have the firewall/proxy server with two nic and just get the firewall to be a DHCP server to assign ip addresses and disable the dhcp server on the router. So then you will have:

Router -- Clients
   |   |
Firewall

Thus all traffic will be forced to go through the firewall and then back to the router to the clients

---

