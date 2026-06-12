---
title: "The first things you do to secure your 7.04 workstation"
date: 2007-07-24
forum: Server Platforms
---

### Post by tim356 on 2007-07-24
I've been playing with Ubuntu for the past few months and am really starting to like it.  I would like to do a complete reinstall though on my workstation as I have butchered many things with all of my playing around.

Anyway, I was wondering what sort of security measures do people take when they first install 7.04?  What is the first tool you install, what are the changes you make to iptables, do you do configure logs and if so, how?

Please post up what you do when you first install Ubuntu on your workstation.

---

### Post by seamless on 2007-07-24
The first thing I do is add:
```
*               soft    core            0
*               soft    nproc           500
*               hard    nproc           750
*               hard    rss             10000
*               -       maxsyslogins    4
*               -       maxlogins       4
*               -       locks           250
```
To /etc/security/limits.conf to prevent [fork bombs]("http://en.wikipedia.org/wiki/Fork_bomb") and runaway processes.

---

### Post by tim356 on 2007-07-24
Why is it that your first priority is preventing fork bombs?  I would have thought these sorts of attacks would be less common than others?

Thanks for your input though.

---

### Post by seamless on 2007-07-25
[QUOTE="tim356"]Why is it that your first priority is preventing fork bombs?[/QUOTE]
It prevents more than just fork bombs. It also prevents run away processes from locking up the entire system. It's just one of those things I do when setting up a new system like disabling un-needed daemons from starting at boot. If I put it off then it probably won't get done.

---

### Post by eentonig on 2007-07-25
Nothing. As long as their are no default service listening for hackers to attack, I don't enable any security measures. Besides a decent password policy that is.

I'm behind a NAT router, so I'm not even that worried about scans and DOS attacks.

When I enable services like ssh, ftp, www, ... The things I do are
installing and configuring
- logcheck: to check all my logging and report those events that might interest me (ie failed and **successfull** logins)
- snort: Intrusion detection monitoring (and response) tool.
- firestarter: where possible, I only allow access to those ip ranges that are required. (Ie. ssh access is only from the public class B network from my work).
- I only open 1 box to the internet. The others I'mm reach via hopping through

---

### Post by elst on 2007-07-25
For my laptop, the first thing that I do is set a password for the boot loader and lock it, which are setting changes in /etc/boot/grub/menu.lst.

The standard Ubuntu installation is pretty secure from network compromise, since there aren't exploitable services, but is vulnerable to anyone with access to the host computer.

---

