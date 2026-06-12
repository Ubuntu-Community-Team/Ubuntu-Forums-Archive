---
title: "Server with 2 interfaces and DDNS"
date: 2008-10-01
forum: Server Platforms
---

### Post by ferarg on 2008-10-01
Hi, I've got a server ith 2 interfaces, and both are connected to internet, one directly and the other behind a router, and my question is:

Can I use one DDNS domain for eth0 and other domain for eth1?

How can I assign one domain to one interface?

Thanks a Lot!

---

### Post by alastair on 2008-10-01
For DDNS, something like ddclient [1] lets you set a specific ethernet device to use for the domain resolution, hence the IP address ti use.

[1] ddclient - lots of options - see the usage page.

[http://ddclient.wiki.sourceforge.net/](http://ddclient.wiki.sourceforge.net/)

---

### Post by ferarg on 2008-10-01
Thanks!

---

