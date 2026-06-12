---
title: "Give Up config Firewall with Ubuntu"
date: 2009-07-08
forum: Server Platforms
---

### Post by tomvietdungvn on 2009-07-08
Please help me!
I have a static Ip:255.255.222.3.I'd like to use iptable to nat this ip to network 192.168.0.0/24.so as to config webser,mail server.

---

### Post by drave99 on 2009-07-09
ipables -t nat -A PREROUTING -p tcp -d 255.255.222.3 --dport 80 -j DNAT --to-destination 192.168.0.0

255.255.222.3 doesnt look like a valid address. 255 is usually broadcast ? 
192.168.0.0 NEEDS A REAL ADDRESS to be a real address

---

### Post by tomvietdungvn on 2009-07-10
> **drave99 said:**
> ipables -t nat -A PREROUTING -p tcp -d 255.255.222.3 --dport 80 -j DNAT --to-destination 192.168.0.0

255.255.222.3 doesnt look like a valid address. 255 is usually broadcast ? 
192.168.0.0 NEEDS A REAL ADDRESS to be a real address

Thanks for your help!
My plan is:
I config eth0 :222.255.17.242
         eth1 :192.168.0.1
         webser:192.168.0.2
         mail server:192.168.0.3
Plese!help me nat and show me more carefull.thanks

---

