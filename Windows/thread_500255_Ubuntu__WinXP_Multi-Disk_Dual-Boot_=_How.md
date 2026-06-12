---
title: "Ubuntu / WinXP Multi-Disk Dual-Boot = How?"
date: 2007-07-13
forum: Windows
---

### Post by Lego Dragon Rider on 2007-07-13
I'm wondering how I can create a dual-boot Ubuntu Feisty ( :) ) / WinXP( :oops: ), using separate hard drives for each OS. Normally, I wouldn't even think of doing it, but I need to use a few non-wine-able  programs.

 Basically, I have 2 brand-new hard drives, and I need Ubuntu on drive 1 and XP on drive 2. So far, so good. The problem I have is how to setup the hardware/bootloader in such a way that I can choose which OS to boot. I personally have no clue whatsoever. Any help?

---

### Post by smoker on 2007-07-13
hi, have a read here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

you basically treat your 2 drives as two partitions, and the info there should help (read to bottom of page),

best of luck.

---

### Post by dorath on 2007-07-15
Lego,

My current setup has Ubuntu on one drive, and XP on a separate drive.  My BIOS is set such that it will try to boot to the drive with Ubuntu (and more importantly, GRUB) first.  GRUB is the bootloader used by Ubuntu.

Here is how I got GRUB to boot XP:
The first step makes a backup copy of menu.lst.  The second step opens menu.lst in a text editor.  Lots of people use nano instead of pico (and there's a bajillion other ways to do it).  Use whatever you're comfortable with.```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo pico /boot/grub/menu.lst
```

This is what I had to add to the very bottom of my /boot/grub/menu.lst:
```
title           XP (Games)
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader     +1
```

Hope that helps!

---

### Post by Lego Dragon Rider on 2007-07-20
Thanks a ton guys! That's exactly the info I need! :)

---

### Post by Lego Dragon Rider on 2007-07-27
I got the machine set up now, and I actually decided to use Freespire instead of Ubuntu. Freespire automatically displays the GRUB screen upon bootup, and the installation is faster. Those are the only real reasons I chose Freespire over Ubuntu, plus I already have one Ubuntu machine and it's good to have some variety. 

I guess this topic is solved. However, this thread can still be useful to other people who need/want a dual-boot machine. Thanks again for all your helpfulness!

---

