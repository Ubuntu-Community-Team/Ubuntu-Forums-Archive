---
title: "PREROUTING, POSTROUTING with shorewall?"
date: 2012-02-21
forum: Security
---

### Post by Nitha88 on 2012-02-21
Hello,

I have a VirtualBox VM running Debian with network in Host-Only mode.
can somebody help me to configure the following iptables command in shorewall:

> [B]
iptables -t nat -I PREROUTING -d 188.40.xxx.xxx -j DNAT --to 192.168.56.101
iptables -t nat -I POSTROUTING -s 192.168.56.101 -j SNAT --to 188.40.xxx.xxx[/B]

thanks

regards
Nitha

---

