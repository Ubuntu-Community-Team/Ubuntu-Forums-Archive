---
title: "USB drive freezes guest - Linux Mint Host, Windows XP guest"
date: 2010-12-07
forum: Virtualisation
---

### Post by caspian915 on 2010-12-07
Hi all,

I've been searching around, but nothing seems to be exactly what I'm looking for. I started from scratch today, loaded Linux Mint, installed VirtualBox, and then installed Windows XP. With some searching and trial and error, I got everything up and running. The XP guest lets me select my external Seagate drive, but when I click on it most of the time Windows Explorer freezes, and even when it doesn't, the drive doesn't show up. It disappears from my Linux Host, so something does work the way it's supposed to. 

What could be the issue here? What more information do I need to provide?

thanks,
sps

---

### Post by lmarmisa on 2010-12-09
I suppose you are using a VirtualBox USB filter for the access to your external Seagate drive.

If you get problems with USB, the shared folders option could be an alternative:

[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

