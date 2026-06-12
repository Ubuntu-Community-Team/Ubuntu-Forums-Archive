---
title: "GIMP starts up and that is about it."
date: 2010-01-23
forum: Ubuntu Studio
---

### Post by SoFl W on 2010-01-23
Late last year I upgraded from 9.04 to 9.10, I also upgraded GRUB about the same time.  The past six months life has kept me very busy so I am getting around to asking a lot of questions.

After my upgrade Gimp would start, load a graphic if requested but none of the functions worked.  There were no layers listed in the layer window and although I could select a brush, or tool those tools would not work.  The program would ask if I wanted to save the changes I made although the graphic remained the same.

I also noticed that SANE would scan but after the lamp returned to the top of the scanner SANE would close never saving or processing the graphic.  This happened with  preview or a full scan.

I remember searching for answers and thought there were similar problems but I can't seem to find those threads now.   

Has anyone else had similar problems with SANE or GIMP?  If so how was the problem resolved?

---

### Post by d3v1150m471c on 2010-01-23
Backup your important files and install 9.10 with the desktop.iso live cd.

---

### Post by SoFl W on 2010-01-23
I performed the upgrade with a live CD, I had actually thought about downgrading back to 9.04. 
I am using a dual boot with Windows.  I will try a reinstall of 9.10 again, but if I remember correctly it didn't offer me the option to over write the ubuntu partition.

---

### Post by SoFl W on 2010-01-30
I found out what the problem was and it was actually two problems.  The first problem was my tablet.  The tablet is a monoprice.com generic tablet which I believe is made by  UC-Logic.   With 9.04 it sort of worked but I never got around to tweaking it.  After the upgrade to ubuntu 9.10 GIMP didn't do much besides load a graphic, once I disabled the tablet in GIMP, GIMP started working.

Which led to my other problem, the layers never showing up.  This was simple enough I went to the "Layers, channels, path" toolbar and selected the correct image at the top.  (see attachment)  For some reason it was blank, now GIMP works fine.

---

