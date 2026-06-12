---
title: "Midori missing into AA archive"
date: 2017-09-17
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-09-17
Searching to install Midori, but the artful archive miss it.
The sources are not compiled since a while: [https://launchpad.net/ubuntu/+source/midori](https://launchpad.net/ubuntu/+source/midori)
and lp:1698483 point to a vala problem

---

### Post by vasa1 on 2017-09-17
I read somewhere that Debian has dropped it.

[https://ubuntuforums.org/showthread.php?t=2369995&p=13681078#post13681078](https://ubuntuforums.org/showthread.php?t=2369995&p=13681078#post13681078) or [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=864951](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=864951)

From the bug page:> 
The final stable release of Midori still uses the unmaintained WebKit1
instead of webkit2gtk and therefore the browser suffers from numerous
known security vulnerabilities. Midori now fails to build with vala
0.36 which is in Ubuntu 17.10 Alpha and will be in Debian unstable
once it clears the Debian new queue.

---

### Post by amano on 2017-09-17
[https://bugs.archlinux.org/task/46333](https://bugs.archlinux.org/task/46333)

Arch could't get it compiled with webkit2 as well :(

---

### Post by dino99 on 2017-09-17
webkit2 is required; so it should not be the real problem
[http://www.linuxfromscratch.org/blfs/view/stable-systemd/xsoft/midori.html](http://www.linuxfromscratch.org/blfs/view/stable-systemd/xsoft/midori.html)

---

### Post by sudodus on 2017-09-17
We would all be happy if somebody does it for us :-P

---

### Post by jbicha on 2017-09-17
Yes, I helped [remove]("https://bugs.debian.org/864951") midori from Debian and Ubuntu. It's not coming back since it's unmaintained.

---

### Post by andrew.46 on 2017-12-24
Enthusiasts can still build their own as has been recently demonstrated by myself [on AskUbuntu...]("https://askubuntu.com/a/989052/57576") Note the warning in this post about midori being unmaintained for some time...

---

### Post by dino99 on 2017-12-24
Thanks for your Christmas gift Andrew ):P

---

### Post by vasa1 on 2017-12-24
Closed. This sub forum is for Ubuntu Development Release and Artful has been released.

---

