---
title: "Executables are not running"
date: 2007-11-07
forum: Server Platforms
---

### Post by tanman77 on 2007-11-07
After a few days, Ubuntu Server does not run any executable properly, save for things such as uptime, ps. If I try to run  top, htop in ssh, they do not work.

At this stage I get good response times from Apache when I browse to it from my browser.

I posted a similar instance here: [http://ubuntuforums.org/showthread.php?t=567573&page=2](http://ubuntuforums.org/showthread.php?t=567573&page=2)
but I think I was beating around the wrong bush there.

Any ideas where I could start to diagnose this problem?

kind regards,

---

### Post by koenn on 2007-11-08
> **tanman77 said:**
> After a few days, Ubuntu Server does not run any executable properly, save for things such as uptime, ps. If I try to run  top, htop in ssh, they do not work.
Any ideas where I could start to diagnose this problem?

You could start with **accurately **describing the problem, in detail.
it's highly unusual for unix commands to fail without feedback, so : what's the feedback ?

---

### Post by tanman77 on 2007-11-11
> **koenn said:**
> You could start with **accurately **describing the problem, in detail.
it's highly unusual for unix commands to fail without feedback, so : what's the feedback ?
Koenn,
Thanks for the reply. Much appreciated. . What I see is the system not responding with anything. After a span of three to four days, I would log into the website that it is hosting or a ssh session...and it just hangs.

I used Munin to do some graphs and it shows 2 active connections through netstat and 0.3 type load.

I could submit the results from munin in a pdf.

Thanks!

---

