---
title: "Iptables rules"
date: 2008-07-23
forum: Security
---

### Post by damatta on 2008-07-23
Hi.
Would you happento know a way to control system behaviour when connection requests are received on TCP or UDP ports where there is no socket listening? I know this can be done using net.inet.tcp.blackhole or net.inet.udp.blackhole in FreeBSD but I'm not aware of anything similar in Linux, so I thought iptables would be the only possibility.

---

### Post by huntzire on 2008-07-24
Well I may be completely in left field, but if your assuming to set a certain rule in iptables, you can use ufw from command line to define what protocol or port can be accepted or denied. 

 Now as far as ufw allowing iptables to provoke system action when the event is triggered, I couldn't really tell you but ill see if I can find something like that on the net.

---

### Post by The Cog on 2008-07-24
How about:
iptables -A OUTPUT -p icmp --icmp-type port-unreachable -J DROP
Haven't tried it, so its just a guess.

---

