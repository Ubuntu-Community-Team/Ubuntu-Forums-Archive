---
title: "cyradm does not allow authentication"
date: 2008-09-16
forum: Server Platforms
---

### Post by BlackHatRob on 2008-09-16
All:

I have attempted to install postfix + cyrus but I have encountered a strange issue. I have configured cyrus to use saslauthd, but when I attempt to log into cyradm, it just sits there never asking me for my password.

root@core:~# cyradm -u cyrus localhost


That's all that happens. Any ideas?

---

### Post by BlackHatRob on 2008-09-16
For those that may come across this... there was a firewall blocking the administrative port for cyrmaster (which happened to be tcp:2000)

---

