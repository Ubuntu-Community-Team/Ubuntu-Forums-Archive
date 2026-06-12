---
title: "My LAMP Server is SLOW!"
date: 2006-08-28
forum: Server Platforms
---

### Post by jmcentire on 2006-08-28
I pulled an older computer off the shelf last week and installed using the LAMP option.  Got my intranet site up and running and it is unbearably slow.  When you first go to the page, sometimes it will take up to 30 seconds to begin loading, but usually once it starts to load the page it is almost instantaneous, sometimes it will pause half way through the page for about 5-10 seconds then finish loading again.  A page with only phpinfo() took about 3-4 minutes to load.  Anyone have ideas? Here is the hardware:
AMD Duron 1300
256 MB
Brand New WD SE 80GB
Intel Pro 100

---

### Post by az on 2006-08-28
I tested a bunch of web applications on a Dapper LAMP stack on a Pentium 1 (166 MHZ) and it was pretty fast.

Are you sure you don't have a hardware problem with your NIC or something?

If you have a desktop envoronment on there, can you browse localhost any better?

---

### Post by Woei on 2006-08-29
> **jmcentire said:**
> I pulled an older computer off the shelf last week and installed using the LAMP option.  Got my intranet site up and running and it is unbearably slow.  When you first go to the page, sometimes it will take up to 30 seconds to begin loading, but usually once it starts to load the page it is almost instantaneous, sometimes it will pause half way through the page for about 5-10 seconds then finish loading again.  A page with only phpinfo() took about 3-4 minutes to load.  Anyone have ideas? Here is the hardware:
AMD Duron 1300
256 MB
Brand New WD SE 80GB
Intel Pro 100

Sounds like a DNS problem. Your machine is probably trying to find an ipv6 network, but can't find a properly configured DNS that will give it the information it wants to do a reverse lookup, and everything will stall until the timeout alarm rings and the same query is done again with IPv4. Try something like described [here](http://www.ossgeeks.co.uk/?p=20) or [here](http://blogs.sun.com/sharps/entry/faster_surfing_with_the_dapper) and try again.

---

