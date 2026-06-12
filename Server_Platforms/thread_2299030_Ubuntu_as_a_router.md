---
title: "Ubuntu as a router"
date: 2015-10-15
forum: Server Platforms
---

### Post by zzixxus on 2015-10-15
Hello,
 I have a problem, I put the router on the server and the DNS does not work automatically.

I need to on Windows and all other computers dns configured to:
8.8.8.8
10.0.0.2

Of course, my server has two network cards, eth0 connected to a router and eth1 connected to a switch

---

### Post by darkod on 2015-10-15
We need more info. Does the routing work? Because if you use ubuntu as a router it has nothing to do with the dns. Your clients still need to know where to find their dns server, either by dhcp options or similar, or static dns.

---

### Post by TheFu on 2015-10-15
DHCP generally provides DNS settings to clients. This can be part of a router config, but it doesn't have to be.  The Windows clients can get DNS settings from DHCP or hard coded inside each machine.

---

