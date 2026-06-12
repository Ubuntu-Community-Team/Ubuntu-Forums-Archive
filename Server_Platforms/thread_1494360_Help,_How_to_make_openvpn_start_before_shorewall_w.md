---
title: "Help, How to make openvpn start before shorewall when boot up"
date: 2010-05-26
forum: Server Platforms
---

### Post by zhangr on 2010-05-26
We have several vpn links, and what I want is make openvpn daemon start before shorewall, since if the vpn interfaces has not been brought up, shorewall can not identify the interfaces and zones, and refused to start. I've tried to set "wait_interface" in /etc/default/shorewall, but I found openvpn start after shorewall, and this method just increase the time cost on boot up.  So howto adjust the rcX.d startup secquence? Seems openvpn and shorewall are in different startup queue (openvpn script link is in rc2.d, and shorewall is in rcS.d). Anyone have a solution?

---

### Post by karesmakro on 2010-05-27
I had the same issue. My solution was, to add a start and stop entry for the shorewall firewall in openvpn init script self, or vice versa.
Reason why for me was, that the iptable entries should be flushed on restarting vpn service anyway.

There are also start and stop firewall scripts in the source of openvpn package to taken into account.

regards

---

### Post by zhangr on 2010-06-01
> **karesmakro said:**
> I had the same issue. My solution was, to add a start and stop entry for the shorewall firewall in openvpn init script self, or vice versa.
Reason why for me was, that the iptable entries should be flushed on restarting vpn service anyway.

There are also start and stop firewall scripts in the source of openvpn package to taken into account.

regards

Okay, seems this is the simplest way to make it working, I've considered this method, just..., I do not want to "destory" the start up scripts comes from distribution. And I hope UBUNTU foundation will bring out a solution in some day future. Thank you alll the same.

P.S.
I've found another solution, add the command you'd like to run at the end of booting into /etc/rc.local

---

