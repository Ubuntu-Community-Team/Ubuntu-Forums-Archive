---
title: "Boot gets stuck on Purple screen."
date: 2011-12-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Mathor on 2011-12-08
My bootloader gets stuck on a purple screen on 12.04 on every boot. The only way to get in is through recovery. I do not have an nvidia card, I have an ATI, and have followed many threads trying to fix it, but to no avail. Other than this, I am loving 12.04. It runs a lot faster for me than 11.10, so I really wouldn't like to downgrade just because booting is a hard process. Please help me!

---

### Post by dino99 on 2011-12-08
from: /etc/default/grub
remove "splash"
then: sudo update-grub

thats let you see the booting verbosery, and watch your logs too (/var/log/ & .xsession-errors into /home (unhide it with ctrl+h))

---

### Post by TDK800 on 2011-12-08
Same here, after today's updates. Nvidia card. Unity doesn't load - keeps switching between purple screen and nvidia splah screen. Any suggestions?

Couldn't even remove splash from grub, says filesystem is read-only.

---

### Post by zika on 2011-12-08
LiveCD, chroot...

---

