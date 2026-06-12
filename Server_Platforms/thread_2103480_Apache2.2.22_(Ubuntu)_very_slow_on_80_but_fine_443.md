---
title: "Apache/2.2.22 (Ubuntu) very slow on 80 but fine 443"
date: 2013-01-10
forum: Server Platforms
---

### Post by M1GEO on 2013-01-10
Hello All

I run a small personal webserver, Apache/2.2.22 (Ubuntu) on Ubuntu Server 12.10.

```
george@tesla:~$ apache2 -version
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Nov  6 2012 20:27:22
```

I have run an apache server since 2005, but I don't really know it in depth; it's always just worked really.  And when it hasn't Googling about sorts it.

But for the last few months, I guess since I upgraded to 12.10, I have some strange issues.

The server responds fine to any connection via SSL on port 443.  However, any request via port 80 is served very very slowly.  Given enough time, it does work, but it takes several minutes to show a simple page.  As I say, simply change the request to https and it's "instant", or seemingly so.

I don't know enough to poke around.  There's nothing in the error or access logs that looks untoward, and there's nothing in the kernel messages (dmesg).

The configuration virtualhost for *:80 and *:443 are virtually identical, apart from the SSL bits; the config files have served me well before.

The server has worked before. With these settings. I noticed the CPU use was very high and that Apache was using a lot, so I restarted it with "service apache2 restart" and now this.

Usually rebooting the server will fix it, but I would be keen to diagnose the problem or at least a more effective solution.

**EDIT:***rebooting the server nolonger fixes the issue.  Please help!*

Thanks all.
George.

---

