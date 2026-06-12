---
title: "Mail Server Hostname"
date: 2009-01-21
forum: Server Platforms
---

### Post by trentscott4 on 2009-01-21
It seems that whenever I use the Ubuntu 8.10 Intrepid Server installation cd (clean install) and select mail server as a software option, the install fails.  Does anyone else experience this issue?

I'm a Comcast subscriber and it detects my hostname as xxx.xxx.comcast.net. (with the trailing dot, which I removed) -- still no luck.  Then, I tried reinstalling and using my fqdn  server.xxxx.com -- no joy.  If I have a dynamic IP and I'm using Zoneedit for my dns and have forwarded server.xxxx.com to my ip address and set up appropriate mx records, isn't that all I need to do?

Should I use something else or is there another reason the install might fail?  Again, it only happens when I select mail server.  If I install LAMP and OpenSSH only (for example), the install finishes.

---

