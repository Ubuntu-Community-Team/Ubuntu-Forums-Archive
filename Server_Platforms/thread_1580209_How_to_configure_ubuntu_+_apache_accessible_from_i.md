---
title: "How to configure ubuntu + apache accessible from internet?"
date: 2010-09-23
forum: Server Platforms
---

### Post by plusnplus on 2010-09-23
Hi..,
i have router, configure with static WAN IP.
i have ubuntu box, configure with LAMP and it is working fine in LAN.
how i should configure the ubuntu, so it become accessible from internet?
am I just edit httpd.conf, change the server name, to WAN IP?

is the ubuntu IP address I need to change to ?

thanks for any guide/ info/ help.

---

### Post by madverb on 2010-09-23
Log into router.
Forward port 80 and 443 to the Ubuntu server.

[http://portforward.com/](http://portforward.com/)

---

### Post by plusnplus on 2010-09-23
> **madverb said:**
> Log into router.
Forward port 80 and 443 to the Ubuntu server.

[http://portforward.com/](http://portforward.com/)

is that all?
no change any setup in ubuntu server?

---

### Post by spynappels on 2010-09-23
Nope, that is all. If everything worked correctly in the local LAN, the server is set up fine, you just need to allow outside stuff to access it, which is what port forwarding does.

---

