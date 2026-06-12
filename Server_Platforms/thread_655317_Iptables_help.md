---
title: "Iptables help"
date: 2008-01-01
forum: Server Platforms
---

### Post by gamerteck on 2008-01-01
Hi,

I have iptable rules setup to block all incoming traffic to my Mythbuntu/file server, stave for my work ip, to SSH, and my LAN mac addresses.

I want to enable port 80 to use Mythweb, which allows me to manage Mythtv through the web, to a certain extent.

LAN access is fine, but external access is not working.  I've searched google but was unable to come up with an answer.

I would like to restrict all external incoming requests to port 80 except for those few ip addresses I deem appropriate.

---

### Post by The Cog on 2008-01-01
You should probably have a default policy to drop incoming packets:
**iptables -P INPUT DROP**
but accept packets for existing connections:
**iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT**
and accept TCP connections to port 80 from selected addresses:
**iptables -A INPUT -p tcp -s 1.2.3.4 --dport 80 -j ACCEPT**

---

### Post by gamerteck on 2008-01-05
Thanks this helped **The Cog**. You pushed be in the right direction.

The end results is:
[B]-A INPUT -p tcp -m tcp --dport 80 -m iprange --src-range 1.2.3.4-2.4.6.8 -m comment --comment "Work IP Range" -j ACCEPT
[/B]

---

