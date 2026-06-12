---
title: "Restrict IP, but allow me to browse"
date: 2007-12-25
forum: Server Platforms
---

### Post by xyloweb on 2007-12-25
I have set up LAMP on my desktop Ubuntu 7.10 PC.
I want the web site to be available only to a few IP addresses that I specify, BUT I still want to be able to browse the internet from this PC.
I've played with ports.conf and iptables, but I can't seem to get the IP restriction working without also cutting off my internet browsing.

**So, how can I restrict who sees my site, but allow me to browse normally?**

Some good posts that have helped, but not solved my problem.
The first one is about mod_access, but does not give enough details on how to implement it.  I cannot find mod_access.so on my system.
[http://ubuntuforums.org/showthread.php?t=484020](http://ubuntuforums.org/showthread.php?t=484020)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by The Cog on 2007-12-26
That's what firewalls are all abut. You can block incoming connections from all but a few IP addresses, but still allow all outgoing connections. Firestarter is the firewall that I think most people use with Ubuntu. It's in the repositories.

---

### Post by xyloweb on 2007-12-26
Thanks for the info, and helping me connect A to B.  I certainly know what a firewall is, but it didn't occur to me that it was what I needed to solve this specific problem.

---

