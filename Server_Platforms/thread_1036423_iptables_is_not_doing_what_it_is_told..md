---
title: "iptables is not doing what it is told."
date: 2009-01-10
forum: Server Platforms
---

### Post by deags on 2009-01-10
it still sends **** via the default interface even though i'm telling it other wise

[IMG]http://img82.imageshack.us/img82/1038/91629062qv2.jpg[/IMG]


how ever i kinda get it working when i do this(trying to force it's hand)

iptables -A PREROUTING -t mangle -i eth0 -s 192.168.1.102 -j MARK --set-mark 1
 iptables -t nat -A POSTROUTING -s 192.168.1.102 -o ppp0 -j SNAT --to-source 60.241.215.178
ip rule add fwmark 1 table TPG

IPTRAF output:
ICMP echo req (60 bytes) from 192.168.1.102 to 206.190.60.37 on eth0
ICMP echo req (60 bytes) from 60.241.215.178 to 206.190.60.37 on ppp0
ICMP echo rply (60 bytes) from 206.190.60.37 to 60.241.215.178 on ppp0

so it gets close in that case but it will not forward the reply to 192.168.1.102

---

### Post by dorowa on 2009-01-16
Ok... may be you can tell what exactly you wanne get from it... just nat or what?

---

