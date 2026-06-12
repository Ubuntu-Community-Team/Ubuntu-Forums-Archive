---
title: "game installation problems"
date: 2009-02-14
forum: Wine
---

### Post by AilesGrises on 2009-02-14
I'm installing Call of Duty 1, which is a game my computer could play when I was running Windows XP, so this should go fairly smoothly after this problem is solved. During installation, when it come time to insert disc 2, a thing comes up saying an application won't let me eject disc 1. It looks like this:

[http://img.photobucket.com/albums/v293/Dark_Jedi_1714/Screenshot.png](http://img.photobucket.com/albums/v293/Dark_Jedi_1714/Screenshot.png)

How can I insert disc 2?

---

### Post by Dizzle7677 on 2009-02-15
Try 'eject <device name>' (ie. eject /media/cdrom0) in the terminal. rtm -> man eject

Workaround: burn the CD's to the disk as ISO's then mount them with Gmount-iso.

---

