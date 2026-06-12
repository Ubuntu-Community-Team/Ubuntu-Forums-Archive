---
title: "Warning: Upgrade to Natty disables IP forwarding in sysctl.conf"
date: 2011-05-26
forum: Server Platforms
---

### Post by hawkmage on 2011-05-26
I have a inet6 v4tunnel interface defined and enabled net.ipv6.conf.all.forwarding in the sysctl.conf file.  Just upgraded to Natty and I noticed my IPv6 tunnel was not routing traffic anymore.  I discovered that the upgrade replaced the sysctl.conf file and IP forwarding was nolonger enabled.

---

