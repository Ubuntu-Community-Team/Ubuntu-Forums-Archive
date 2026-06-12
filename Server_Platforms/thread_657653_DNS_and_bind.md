---
title: "DNS and bind"
date: 2008-01-03
forum: Server Platforms
---

### Post by Th0rn0 on 2008-01-03
Hi all, Having a problem. 

I followed this tutorial
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

Set it up as it said (although not sure on the ISP DNS but not sure where to get it (I'm on plus net))

anyway, set it to linux.lan. Does not work.

Ubuntu 7.04. Using Bind9, used the IP 192.168.0.200

Any help please.

---

### Post by metoor30 on 2008-01-07
You need the IP address of your ISP DNS servers.  This will allow your DNS server to forward queries for domains which you do not own and resolve them for you.  If you have a home network with a router, check in the router web interface or on a DHCP client for the proper DNS server.  If you are working out of the office, I would contact your ISP.

---

