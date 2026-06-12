---
title: "Vista Headaches."
date: 2006-09-20
forum: Windows
---

### Post by Apotheosis on 2006-09-20
I recently got Vista to check it out.  After installing I noticed that Microsoft being the controlling pricks they are decided you don't need any other OSs on your system.  Windows overwrote Grub and I want it back.  I followed a link on here that took me to a place to re-install Grub and make it my primary bootloader, but that requires me to be in Ubuntu.  Something I can not accomplish given my current situation.  Please tell me I will not have to re-install Ubuntu... :(

While you are at it, you can tell me how to get Grub back too. ;)  Thanks in advance.

---

### Post by Rumor on 2006-09-20
I believe that if you boot the live/installer CD, you can open a terminal window and follow the instructions you mentioned to reinstall grub.

This thread might help: [http://www.ubuntuforums.org/showthread.php?t=256209](http://www.ubuntuforums.org/showthread.php?t=256209)

edited for spelling

---

### Post by Apotheosis on 2006-09-20
God, you don't know how happy I was to see that it worked.  I almost jumped in the air for joy, literally.  Thanks a bunch for your help.

Just incase anyone stumbles across this thread sometime in the future, I ended up using [this]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub") thread to do the deed.

---

### Post by 3rdalbum on 2006-09-21
Mac OS does the same sort of thing: If you boot from a Mac OS CD, as well as installing Mac OS, it stops the computer from going into Yaboot by default. Fortunately, you can always go into Open Firmware and type:

boot hd:*x*,yaboot

where *x* is the partition number of the bootloader. Then once you're in Ubuntu, you can just type ybin and off you go again.

---

