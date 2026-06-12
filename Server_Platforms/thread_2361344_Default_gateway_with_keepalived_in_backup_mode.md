---
title: "Default gateway with keepalived in backup mode"
date: 2017-05-15
forum: Server Platforms
---

### Post by Kjeld Flarup on 2017-05-15
I have two servers running keepalived

When entering MASTER it sets default gateway
virtual_routes {        
default via 194.247.61.254 dev eth0.200    
}

Now I want to use another default gateway in backup. How to?
I tried to put a default in /etc/network/interfaces, but then the MASTER gateways is not chosen when it is MASTER.

---

