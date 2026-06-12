---
title: "Permitting a Network using Firestarter"
date: 2008-12-19
forum: Security
---

### Post by bigjon00 on 2008-12-19
I have a question regarding the firestarter policy definition in version 8. According to the policy dialog I can define a "network" - how is the question.  I only managed to define a single IP address or name. I want to define a network (maybe with a subnet). Found nothing on the web regarding this. Can anyone help????

---

### Post by The Cog on 2008-12-19
iptables uses /mask notation so I guess firestarter uses the same. e.g. 192.168.0.0/24 means a 24 bit network number, 192.168.0.0 to 192.168.0.255.

---

