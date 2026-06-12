---
title: "Unable to open tomcat port"
date: 2008-05-15
forum: Server Platforms
---

### Post by kankuman on 2008-05-15
I am unable to open tomcat5.5 port 8180 to make my pages accessible from other computers (throw internet).
I have the tomcat5.5 service started and am able to access it locally from my computer, but not from other computers.

Here is the output of nstat:
root@mikel-desktop:/home/mikel# netstat -an | grep 8180
tcp6       0      0 :::8180                 :::*          ESCUCHAR   

* 'Escuchar' means 'listen' in spanish



I have tried to open port 8180 by using:
iptables -A INPUT -p tcp -i eth0 --dport 8180 -j ACCEPT
but I don't fix anything doing this.
On the other hand I have Apache2 properly configured and working fine.

I would be thankful for your replies, 
Thanks!

---

