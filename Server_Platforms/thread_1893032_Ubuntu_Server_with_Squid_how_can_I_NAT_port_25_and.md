---
title: "Ubuntu Server with Squid: how can I NAT port 25 and 110?"
date: 2011-12-09
forum: Server Platforms
---

### Post by LtPitt on 2011-12-09
Hello there!

I've setup a lovely Proxy Server on Ubuntu: works simply great.

Now I neet to nat port 25 and 110 to allow my windows outlook clients to reach pop3 and smtp server...

What should I do?

Thanks!

---

### Post by LtPitt on 2011-12-09
Hoooorray! :D


iptables -t nat -A POSTROUTING -p TCP --dport 25 -j MASQUERADE 
iptables -t nat -A POSTROUTING -p TCP --dport 110 -j MASQUERADE 


did the job

---

### Post by LtPitt on 2012-01-20
--
Added this reply for error: sorry.

---

