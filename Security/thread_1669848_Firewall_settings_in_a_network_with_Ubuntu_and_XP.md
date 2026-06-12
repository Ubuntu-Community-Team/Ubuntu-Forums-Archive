---
title: "Firewall settings in a network with Ubuntu and XP"
date: 2011-01-18
forum: Security
---

### Post by Alver on 2011-01-18
Hello forum members,
 I run a small (cabled) network between a desktop with XP with two printers hooked to it and a laptop with Ubuntu 10.04.1 64b. I can approach and use these printers from my laptop and filesharing works also. BUT ... this only works when my Ubuntu firewall (Gufw 10.04.5) is switched off. I am operating behind my router_modem which has a hardware type of firewall switched on at all times so I presume I'm safe. Now my questions:
1. Is this really safe enough?
2. What kind of settings would Gufw need to be able to use it AND use my mini-network for printing? I have no experience whatsoever with firewall rules and settings.

All help and practical hints are most welcome

Alver

---

### Post by mikewhatever on 2011-01-18
The question is, why you need a firewall on Ubuntu in the first place. There aren't any open ports by default, and hence, nothing to firewall, that is, unless you've installed and run servers there. 
If you do need a firewall, allow the local network ips, like 192.168.*.*.

---

