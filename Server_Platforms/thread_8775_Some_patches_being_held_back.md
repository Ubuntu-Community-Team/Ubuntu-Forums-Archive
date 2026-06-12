---
title: "Some patches being held back"
date: 2004-12-20
forum: Server Platforms
---

### Post by infornography on 2004-12-20
When I do an update using 'sudo apt-get update' and 'sudo apt-get upgrade' it all works fine, but I get the following notice:

The following packages have been kept back:
  linux-image-2.6-386 linux-restricted-modules-2.6-386

Why are those two packages being left back? Is there any way I can force them to update, or would that be a bad idea?

Just curious...

---

### Post by ubuntu_demon on 2004-12-21
Are you using hoary ? If you're using hoary this thread should be moved to the "Hoary Hedgehog Development Release" subforum.

When using hoary pathes are being held back often.  You should give some more info.

This may be relevant :

your opinion: go back to warty, or stay with hoary?
[http://www.ubuntuforums.org/showthread.php?t=7765](http://www.ubuntuforums.org/showthread.php?t=7765)

---

### Post by jdong on 2004-12-21
try an apt-get install on the individual packages, and you'll get a better reason why they're being held back.

---

### Post by Johan on 2004-12-21
[QUOTE=infornography]When I do an update using 'sudo apt-get update' and 'sudo apt-get upgrade' it all works fine, but I get the following notice:[/QUOTE]

 You can try to use the apt-get dist-upgrade command instead. It might remove some packages but is also less likely to hold back upgrades.

---

### Post by nocturn on 2004-12-22
[QUOTE=infornography]When I do an update using 'sudo apt-get update' and 'sudo apt-get upgrade' it all works fine, but I get the following notice:

The following packages have been kept back:
  linux-image-2.6-386 linux-restricted-modules-2.6-386

Why are those two packages being left back? Is there any way I can force them to update, or would that be a bad idea?

Just curious...[/QUOTE]

I get this too.
I installed yesterday.  I'm using a clean warty install.

---

