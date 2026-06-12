---
title: "Hide DNS internal ip addresses"
date: 2009-10-15
forum: Server Platforms
---

### Post by kevin11951 on 2009-10-15
While running my own dns server I noticed that some dns servers can see me, and some cant.  I had no idea why until open dns showed me that it is "safer" to block dns servers that show the internal ip.

how do I stop bind from showing the internal ip, and/or unblock my domain from other dns servers.

---

### Post by kuda on 2009-10-16
I don't know anything about your configuration but one solution to achieve this is split dns config between internal and external view - very very useful, than you can configure via acl and various match-* options who (and what) is able to see you both from LAN and WAN. Please check this one or google it with keywords "bind view"
[http://www.zytrax.com/books/dns/ch7/view.html](http://www.zytrax.com/books/dns/ch7/view.html)

---

