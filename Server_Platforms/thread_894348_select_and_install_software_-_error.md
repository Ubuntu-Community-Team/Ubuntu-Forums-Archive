---
title: "select and install software - error?"
date: 2008-08-19
forum: Server Platforms
---

### Post by GodsDead on 2008-08-19
hey all, im trying to install the latest release of ubuntu server edition, everything runs smooth until i hit the "install software" i have tryed without anything extra but it still gives me an "Error" try again message, and no other information =[

i intended to install the LAMP, mail, samba

help please!

---

### Post by Krupski on 2008-08-19
> **GodsDead said:**
> hey all, im trying to install the latest release of ubuntu server edition, everything runs smooth until i hit the "install software" i have tryed without anything extra but it still gives me an "Error" try again message, and no other information =[

i intended to install the LAMP, mail, samba

help please!

I've run into this problem too. I don't know if this will help you, but here's what my problem was and the solution for it:

I keep an install of Kbuntu on a USB hard drive so that I can experiment with it. It's my "disposable" installation.

Anyway, I found that IF the USB hard drive is plugged into my computer WHILE booting the install CD, the install fails during "Select and Install".

But, if I boot the CD first, THEN plug in the USB drive, the install works fine.

So... if you are trying to install to a fixed disk (i.e. a hard drive in your computer), try going into your BIOS and be sure "Boot from CD" is the first available option. Also if you have it, temporarily disable "Boot USB devices first" (in the BIOS).

My GUESS is that some random junk is being loaded at boot time BEFORE the install CD kicks in and something in memory gets corrupted.

Hope this helps...

-- Roger

---

### Post by GodsDead on 2008-10-03
Right the way i got my system to work, was with a new HDD and a slave one..
have no idea why this would make a difference?

---

