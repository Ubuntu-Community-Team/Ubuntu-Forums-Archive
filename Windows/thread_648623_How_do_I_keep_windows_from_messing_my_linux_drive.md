---
title: "How do I keep windows from messing my linux drive?"
date: 2007-12-23
forum: Windows
---

### Post by dpar on 2007-12-23
I'm almost embarrassed to ask this......:oops: 

My wife wants to play some Windblows games, so I have to install XP for her.
I got an extra 80g drive so that I can keep that microsoft stuff as far away from my Linux as possible.:)
When I try to install to the 80g, which is the slave drive, it wants to install some stuff on my Linux drive, which is the master. Uh, uh....not on my watch your not.....
How can I get this invasive software onto its own drive without touching Linux, and get grub to boot it?

---

### Post by davidgarcin on 2007-12-23
No matter what, XP is going to overwrite your Master Boot Record.  That should be the only thing it tries to change on your master drive, unless you are setting it up very differently.

You can let XP change the MBR, then reinstall GRUB to the MBR using these instructions:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once you've got GRUB reinstalled and you can boot to linux, you need to add an entry in GRUB for XP. To do this, edit your /boot/grub/menu.lst and add an entry as follows:

title Windows XP
rootnoverify (hdx,y)
chainloader +1
makeactive

Where x is the number of the hard drive (numbering starts at 0), and y is the number of the partition (again, starting at zero).

-David

---

### Post by dpar on 2007-12-23
Thanks david, got her goin.

---

