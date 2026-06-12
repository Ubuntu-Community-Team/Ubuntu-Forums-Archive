---
title: "Connection Limits"
date: 2017-05-09
forum: Server Platforms
---

### Post by systemgvp on 2017-05-09
Hello to everyone, I'm setting up a server and wondering if exists in ubuntu a command like windows

**net config server**

Which allows you to see the limit of simultaneous input connections

And if there is a difference, on this limitation, between the server version and the desktop.

---

### Post by wildmanne39 on 2017-05-09
*Thread moved to **Server Platforms**.*

---

### Post by The Cog on 2017-05-09
I found this page that suggests the limit might be the number of open file (for a single process).
[http://stackoverflow.com/questions/410616/increasing-the-maximum-number-of-tcp-ip-connections-in-linux](http://stackoverflow.com/questions/410616/increasing-the-maximum-number-of-tcp-ip-connections-in-linux)
Looks like 1024 by default.
This page suggests how you might do that:
[http://www.lognormal.com/blog/2012/09/27/linux-tcpip-tuning/](http://www.lognormal.com/blog/2012/09/27/linux-tcpip-tuning/)

---

