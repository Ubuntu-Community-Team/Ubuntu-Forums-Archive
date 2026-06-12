---
title: "Strange bug in moving my .cache directory to ram (tmpfs)"
date: 2014-01-19
forum: Ubuntu Development Version
---

### Post by spupazza on 2014-01-19
If I move my cache directory to ram (adding this line in the /etc/fstab -'p' is my username :
 *tmpfs /home/p/.cahce tmpfs defaults,noatime 0 0* )

on my next reboot I get black screen and no desktop.
It's strange as I always used to move the .cache directory to ram and never had this issue.
I'd be grateful if anyone could try and check if you get the same issue.
If that happen, it's easy to fix: just log in recovery mode on your reboot, and cancel the addition to the /etc/fstab.

---

