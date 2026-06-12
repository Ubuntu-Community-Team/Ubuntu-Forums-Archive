---
title: "Workgroups to domains"
date: 2008-11-30
forum: Server Platforms
---

### Post by happyhacker on 2008-11-30
I have a single server 8.10 and am currently configuring the network using Webmin, Samba, etc. There are a number of XP Home PCs in the network.

Should I be using workgroups to configure file sharing or a directory service (which I understand requires the PCs to be setup for domains)?

Am I also right in thinking that this is notpossible with XP Home in some way and that can only use workgroups?

I would rather start off with the right network configuration now rather than discover later I need a massive reconfiguration to expand or introduce more features.

---

### Post by HermanAB on 2008-11-30
Correct - XP Home doesn't support Domain authentication.

Note that domain auth really only becomes useful if you have more than about 10 machines.

Cheers,

H.

---

### Post by happyhacker on 2008-12-01
So stick with workgroups. In fact only about 6 PCs max are switched on at one time. What equipment will I need to subnet some of these computers? Currently we only have one router DG834 and a basic switch.

---

