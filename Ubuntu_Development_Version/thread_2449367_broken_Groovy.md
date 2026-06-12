---
title: "broken Groovy"
date: 2020-08-25
forum: Ubuntu Development Version
---

### Post by dino99 on 2020-08-25
Hello,

Seems the latest libffi* package update has broken some package upgrade (python3.8 for example). Groovy can't be fixed by itself: the boot process is ok, get the grub menu, but then the login screen fails to load/open. Even trying to boot from recovery mode fails: can't get the recovery menu.

So i'm trying now to get new updates from a focal chroot: an other problem appear, get 'fail to fetch ubuntu archive'. Looks like i need some nameserver address, but this old school solution is outdated now with systemd (no more /etc/resolv.conf) .

How to bypass this issue ? If someone knows the solution, please share it.

---

### Post by VMC on 2020-08-25
Not sure what that's use for. Says libffi is a foreign function interface library. I'm not compiling anything. I'm not infected.
Latest update shows:```
libffi-checklib-perl/groovy,groovy 0.27-1 all
libffi-dev/groovy 3.3-4 amd64
libffi-dev/groovy 3.3-4 i386
libffi-platypus-perl/groovy 1.31-1 amd64
libffi7/groovy,now 3.3-4 amd64 [installed,automatic]
libffi7/groovy 3.3-4 i386
libffindex0-dev/groovy 0.9.9.9-3 amd64
libffindex0/groovy 0.9.9.9-3 amd64
```

---

### Post by zebra2 on 2020-08-26
I had the same problem this past weekend. Endless loop at login prompt.  I got a /root out of space warning. I use a separate /home partition on my systems  so  I consolidated /swap, /boot, and /root into one single /root partition and formatted with WK4. This removal of the /Swap changes my system to a swapfile instead of swap partition. Reinstalled and everything is working just fine. I think in the future I will double my /root to about 50Gig. Since the advent of terabyte hard drives this is no big deal. Don't know if this helps you but I am and always have been preset to reinstall in 15 minutes or less.

---

### Post by mc4man on 2020-08-26
Most likely nothing to do with  libffi source package upgrades, everything to do with blindly using the  -proposed repo.
How to fix?, do a fresh install, use -proposed package specific or not at all.

(- if one was to enable -proposed today & do a full updare/upgrade te system will not be usable upon rebooting..

---

### Post by dino99 on 2020-08-26
Thanks for the answers

but i'm looking to get a working chroot on a systemd install  :mad:

---

### Post by zebra2 on 2020-08-26
If one is using a Development Ubuntu STOP I think the forum should rename this section to "Unstable".  If one is using an Unstable release of Linux their curiosity should allow them to run the release in any unstable fashion they choose.  There used to be users in this section that intentionally tried to crash their install. It was called "testing" or something like that. Proposed enabled or proposed not enabled is a matter of risk tolerance.  Back in the old days the grandparents would say "You made your bed, sleep in it". I say "Life is good, live it! Just be ready to reinstall. 
PS I'm ready.

---

### Post by zebra2 on 2020-08-26
Now I remember why my Groovy crashed. It was the 2nd reboot after I installed the 5.8 Mainline kernel.  Backing up to the default kernel after that didn't help. I also could not get to root or even a safemode login.  Just reinstalled and got on with my life.  If it happens again I will investigate further. I have a lot of computers so it was no big deal at the time.

PS the error reported by the system was "root out of space".

---

### Post by zebra2 on 2020-08-26
Yep, its proposed verified. If you have it up and running don't update with proposed enabled.

---

### Post by zebra2 on 2020-08-26
Have reinstalled, this time without formatting root to save time. I run legacy not efi and it gives me a "probably not boot" at the end of the install but it boots anyway.  Running updates now without proposed enabled. May be tomorrow before I report.  Have to go to work in a bit.

---

### Post by zebra2 on 2020-08-26
Ok, fully updated with proposed disabled. Running Gnome/Wayland  session with no problems.
So, proposed strikes again. Been awhile, we deserve it.

---

### Post by Cheltspy on 2020-08-26
It looks like gnome-shell has segfault.

gnome-shell[1190]: segfault at 7f742163bb10 ip 00007f742163a1dd sp 00007fffedd41790 error 7 in libgjs.so.0.0.0[7f7421614000+87000]

---

### Post by Cheltspy on 2020-08-27
Proposed is back up now, libffi7:amd64 (3.3-4) was removed and libgjs0g updated.

---

