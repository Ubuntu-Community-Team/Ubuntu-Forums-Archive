---
title: "iowait +/-100%"
date: 2006-05-05
forum: Server Platforms
---

### Post by lvanderree on 2006-05-05
Hello all,

I switched my server from Debian Sarge to Ubuntu Dapper Drake and I know this is still a testing version, but that should be only for a month or so.
I have an, in my opinion, very strange problem: my iowait sometimes is nearly 100% for something like 5-15 seconds.

[IMG]http://www.fun4me.demon.nl/iowait.gif[/IMG]

I especially notice this when opening a page from gallery2 from the server. The thumbnails should already have been made, so all it has to do is getting the thumbs and send them to my browser, but this sometimes cost 15s to return the beginning of the page.
With gallery2 is I have noticed this problem, but I think also dselect has this problem when I look at the packages (select) or leave that overview again.

I'm running Apache2-mpm-preform, (libapache2-mod)php5, mysql5 with kernel-package  2.6.15-21-686 #1 SMP PREEMPT on an ordinary Intel Pentium III (Coppermine) 864Mhz

Does anyone know what might cause this problem?
Thanks in advance

---

