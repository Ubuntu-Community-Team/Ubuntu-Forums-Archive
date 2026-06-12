---
title: "How to keep my server up to date?"
date: 2008-08-06
forum: Server Platforms
---

### Post by DJ_Cyberdance on 2008-08-06
Hi!
I have been using Debian on my desktop pcs for quite some time now and I appreciate the auto update function. Now I switched from Debian to Ubuntu and I wonder if there is something similar like that update notification on an Ubuntu server. As there is no GUI I wonder what options I do have to install security and other updates on a regular basis? I mean how do I stay informed about available security updates? Is there some kind of mailing list or something similar as there naturally is no notification icon on an Ubuntu server?

---

### Post by moonpup on 2008-08-06
You are correct there is no notification... just simply do the following from the command line.

sudo apt-get update

sudo apt-get upgrade

The first line updates the sources lists / mirrors and the second line actually looks for upgrades to installed packages.

---

### Post by StickyStyle on 2008-08-06
The package cron-apt should do what you want, it will email you when an update is available the server it is run on.
[http://www.debian-administration.org/articles/162](http://www.debian-administration.org/articles/162)

For mailing lists there is ubuntu-security-announce, and bugtraq, every admin should be on both.

[http://www.securityfocus.com/archive/1](http://www.securityfocus.com/archive/1)
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

### Post by moonpup on 2008-08-06
I wasn't aware of cron-apt... that's pretty cool and I learned something new, thanks!

---

