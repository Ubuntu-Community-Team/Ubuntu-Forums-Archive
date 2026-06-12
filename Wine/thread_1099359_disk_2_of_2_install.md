---
title: "disk 2 of 2 install"
date: 2009-03-18
forum: Wine
---

### Post by wlraider70 on 2009-03-18
first im a pretty big wine noob...

I have a game that has two install disks, 
after disk 1 is done it says please eject and insert disk two.

I've had several issues and tried a few things.

at first i couldn't eject the the disk because it wouldn't unmount, then i got the cd to open but it didn't seem to notice the new disk

so i made disk 2 into an iso and mounted it, that didn't work

so i made disk 1 into an iso and mounted it, but it wont mount as a CD rom just a folder(i think)

so i looked up mounting as a cdrom and that showed me the winecfg dives tab, but i don't know how to add a cd rom there either.

??

---

### Post by cogadh on 2009-03-18
Next time you need to switch disks, open a terminal window and run "wine eject -a". That will make Wine unmount and eject the disk, which should allow you to put in the second disk and proceed with the install.

HOWEVER...

It doesn't always work, so it might help if you told us what game you are trying to install or looked the game up on Wine's [Application Database]("http://appdb.winehq.org/"), to see if there are any specific alternate instructions you need to follow.

---

