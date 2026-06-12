---
title: "Is there some problem?"
date: 2006-01-22
forum: Server Platforms
---

### Post by Elvish Legion on 2006-01-22
Well as soon as I turn on my computer and firewall I get a hit...so far I've gotten 5 hits in as many minutes....is this good or bad? Should I swith Firewalls (firstarter is my current).  ShouldI be concerned or is this just script kiddings going at it and bots?

---

### Post by imagine on 2006-01-23
You didn't provide any details. Is your Ubuntu-box connected directly to the modem (internet) or do you use a router/proxy? Did you install any services like a ftp-daemon, apache, sshd, etc which need to be accessed from the internet? By default Ubuntu doesn't listen on any ports to the outside, so setting up a personal firewall isn't really necessary.


Basically: Don't offer any services to the outside which aren't needed, and secure the one which you need.
You don't have to mind about failed login and access attempts. After all they just show that someone could *not* break into your system.

---

### Post by LordHunter317 on 2006-01-23
Unless you're running servers, you don't even need a firewall installed (and maybe not even then).

At anyrate, I'm 99% certain whatever it was can be ignored.  It's just the nature of the Internet.

---

