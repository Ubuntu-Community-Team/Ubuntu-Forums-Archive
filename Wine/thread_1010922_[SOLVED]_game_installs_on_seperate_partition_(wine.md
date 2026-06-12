---
title: "[SOLVED] game installs on seperate partition (wine)"
date: 2008-12-14
forum: Wine
---

### Post by SnakeHips on 2008-12-14
Hi,

I'm trying to install HL2 through Wine......problem is Wine wants to install it to the default drive_c which lacks disk-space. I want to install HL2 to a different partition. How do you guys do it?

---

### Post by Gabt on 2008-12-14
[http://ubuntuforums.org/showthread.php?t=624170](http://ubuntuforums.org/showthread.php?t=624170)

---

### Post by soluphobe on 2008-12-14
Anyway, now that it's moved:


Have you tried going into winecfg > drives defining a new drive path that maps to your new partition?  That way the installer file should see a link to a fake windows partition that links to a real linux partition.

---

### Post by SnakeHips on 2008-12-14
:-) yeah I've tried a load of combinations to get a fix for this. In winecfg the "C:" points to ...drive_C (in my home directory) ,ideally i'd like to move this somewhere else.............. alas it's greyed out :-) seems it's unmovable?? 

Surely I cant be the only gamer that wants to install stuff somewhere other than my home partition...

---

### Post by SnakeHips on 2008-12-16
fix:

move drive_c folder to where you want it

then create symbolic link in terminal
  
ln -s -T /path to/new/drive_c /home/your username/.wine/drive_c

---

