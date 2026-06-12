---
title: "XP Home, problem."
date: 2008-09-16
forum: Windows
---

### Post by Solais on 2008-09-16
Ok summary: got bored of xp, wanted to try vista. Tried vista, after 28 days my trial was gonna be over, so I put the XP Home cd and hit Install from the PC Setup thing (boot from cd). it said i couldnt detect my hard drive, so i went to vista and researched it on google, and it edned up saying they do that un purpose so you dont go back to xp, so i used the DBAN, to completelly delete my hard drive. I booted xp home cd again and it said the same thing, i put linux live cd and after a while i could install it, so after i week i try xp again, and it still couldnt detect my hard drive. May anyone help me? I made a thread about this but forgot to put details :(:(

---

### Post by aysiu on 2008-09-17
Maybe use the Linux live CD to reformat the drive as FAT32 or NTFS and then try to reinstall XP?

---

### Post by karellen on 2008-09-17
do you happen to have sata hard drive? sometimes XP doesn't recognize sata hard disks, if so, you'll need to search for XP drivers of the manufacturer's site, put them on a floppy and then insert the floppy when you install XP

---

### Post by jaqie on 2008-09-17
> **karellen said:**
> do you happen to have sata hard drive? sometimes XP doesn't recognize sata hard disks, if so, you'll need to search for XP drivers of the manufacturer's site, put them on a floppy and then insert the floppy when you install XP
Bingo. XP pre SP2 (almost all the install and restore CDs out there) have no generic SATA drivers. what you need is the "textmode windows xp sata driver" for your SATA controller that is on your motherboard.  This can be fine 98% of the time at the mother board manufacturer's site, once you drill down to the page specifically for files for your particular motherboard model.  Drop those files onto a floppy disc, and use F6 when it says to when windows install is first starting up and says "press F6 to install third party...".

Another option is to use nLite to slipstream in SP2 (or sp3, which would be better) into your windows xp home install CD (by making an iso of it... using nlite to slipstream the data in to the files copied from your cd to hdd as nLite instructs, running the sp2 redist as they instruct, creating an iso of the modified xp install disk, and burning that iso to a CDR disc).

---

### Post by Solais on 2008-09-17
> **aysiu said:**
> Maybe use the Linux live CD to reformat the drive as FAT32 or NTFS and then try to reinstall XP?

I did that :), thats how I installed Linux cause it wouldn't even let me install Linux at the time lol.

---

### Post by technotitclan on 2008-09-17
sp2 doesn't have any sata drivers and to the best of my knowlage neither does sp3, i had to help someone a mounth ago slipstream sata drivers into a brand new copy of xp. as far as i know there are no sata drivers native to xp, the mobo maker provides them.

what is the make, model and year of your computer? or is it home built?

---

### Post by jaqie on 2008-09-17
> **technotitclan said:**
> sp2 doesn't have any sata drivers
It has generic SATA drivers built into SP2, which work for some controllers, but not others. This is why I mention both methods along with being able to slipstream third party textmode drivers with nLite.

---

### Post by technotitclan on 2008-09-17
you made another thread like a day ago or something about the same thing were you did clearify that it IS a SATA hdd. could you please specify the make and model of the sys.


[http://ubuntuforums.org/showthread.php?t=921905](http://ubuntuforums.org/showthread.php?t=921905)

---

### Post by Louis de Broglie on 2008-09-18
I did have such problem. I fixed this by booting from ubuntu live CD. Then I formatted the Vista drive by gparted . Then I booted from XP CD and it worked .:)

---

