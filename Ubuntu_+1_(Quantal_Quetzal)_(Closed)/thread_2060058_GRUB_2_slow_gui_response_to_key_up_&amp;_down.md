---
title: "GRUB 2: slow gui response to key up &amp; down"
date: 2012-09-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by bird1500 on 2012-09-19
Hi,
it seems slow to respond to up and down key presses. Is it considered a bug or a feature?

It's interesting that the reaction to the first key press is slower than to the later ones.
Overall it feels like interacting with a 30 years old computer.

GRUB 1.99 in 12.04 was slightly slow, but GRUB 2.0 from 12.10 is even slower.

---

### Post by lucazade on 2012-09-19
seen this behaviour in an old ubuntu release and it was related to grub resolution.
try to lower the resolution to see if help:

sudo nano /etc/default/grub

find the line
#GRUB_GFXMODE=640x480

remove the #, save and update-grub with:
sudo update-grub

restart and look if it is faster.

---

### Post by ELD on 2012-09-19
Same issue here don't see why it is based on resolution that hasn't changed for me.

Quite annoying.

---

### Post by bird1500 on 2012-09-19
> **lucazade said:**
> seen this behaviour in an old ubuntu release and it was related to grub resolution.
try to lower the resolution to see if help:

sudo nano /etc/default/grub

find the line
#GRUB_GFXMODE=640x480

remove the #, save and update-grub with:
sudo update-grub

restart and look if it is faster.

Thanks, but it shouldn't be dependent on resolution, I'd rather cope with it than do low level tinkering considering that I'll have to do it once in a while each time a new update of grub arrives thru updates.

Windows 7 doesn't have this issue, so I'd rather see this fixed.

---

### Post by funicorn on 2012-09-19
same here. For higher resolution, I can give up speed. what really bothers is the cpu usage. I can hear clearly cpu fan running. That's the problem.

---

### Post by dino99 on 2012-09-19
grub2.0 does not use the same pathes for installation than 1.99
So you might purge grub on your system, then search "grub" with nautilus, to clean the old things left behind.
Then reinstall grub2.0 and finally test again with a new reboot.

---

### Post by funicorn on 2012-09-19
when grub 2.00 is upgrade, there's no instruction to update  /etc/default/grub&#65292;could you please post the original grub 2.00 copy ?

> **dino99 said:**
> grub2.0 does not use the same pathes for installation than 1.99
So you might purge grub on your system, then search "grub" with nautilus, to clean the old things left behind.
Then reinstall grub2.0 and finally test again with a new reboot.

---

### Post by dino99 on 2012-09-19
you does not have to worry about /etc/default/grub , grub installation will built it cleanly.

Start with : sudo apt-get purge grub-pc
( or easier: open synaptic to purge the installed grub packages)
then follow my previous post.

---

