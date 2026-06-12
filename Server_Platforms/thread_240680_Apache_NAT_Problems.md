---
title: "Apache NAT Problems"
date: 2006-08-21
forum: Server Platforms
---

### Post by ByronJC on 2006-08-21
Hi everyone,

Having a problem here, I'm running a web server on my ubuntu server which people from the outside are able to view OK, but when I attempt to view it from inside the LAN it won't work all I get is connection refused.

I noticed when I switched ADSL routers I was able to view my website from inside the LAN so it that telling me the NAT protocol on the router depending on which I use could have a problem or is it my own firewall settings that I could possibly amend which would fix this issue?

Thanks.

---

### Post by ByronJC on 2006-08-21
Nevermind I've figured out the problem....

One of my routers doesn't support loopback which is really annoying.

---

### Post by Sam on 2006-08-21
Add the local hosts in /etc/hosts and you'll be able to access them with their host name instead of IP address.

---

### Post by ByronJC on 2006-08-21
Yeah I did that when I quickly learnt the router doesn't support the loopback feature ... hopefully I can request it for the next firmware upgrade!

---

