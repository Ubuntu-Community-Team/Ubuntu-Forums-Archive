---
title: "Firewall"
date: 2006-05-19
forum: Server Platforms
---

### Post by Coruba67 on 2006-05-19
Hi guys,

Have a fairly simple question to ask... was wondering where the config files are to edit firewall settings. I need to open up port and have no idea how to do it from terminal... I can only SSH into the box as I have no physical access to it... its waaaaaaay up north... 

Cheers for your help in advance!

---

### Post by Jason_25 on 2006-05-19
Normally you edit iptables directly from the command line.  If you want to have it done automatically at boot time you can make an init script for it.

Here's a good link.
[http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-7.html](http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-7.html)

---

