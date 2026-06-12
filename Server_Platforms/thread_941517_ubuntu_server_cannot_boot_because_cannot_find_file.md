---
title: "ubuntu server cannot boot because cannot find file 06"
date: 2008-10-08
forum: Server Platforms
---

### Post by pterandon on 2008-10-08
Hello.
As a self-training exercise, I tried ubuntu server 8.04.1.  The installation appeared to have gone well.  

Upon reboot, the system successfully showed me the GRUB screen. The next screen is black with the text,  (repeated from my memory)
 [FONT="Fixedsys"]"Ubuntu cannot boot because it cannot find on this partition the the file: 06." [/FONT]

Any ideas?  (I went ahead and installed regular ubuntu on top of it, but am wondering what I might have done wrong for the next time I try it.)

---

### Post by Krupski on 2008-10-08
> **pterandon said:**
> Hello.
As a self-training exercise, I tried ubuntu server 8.04.1.  The installation appeared to have gone well.  

Upon reboot, the system successfully showed me the GRUB screen. The next screen is black with the text,  (repeated from my memory)
 [FONT="Fixedsys"]"Ubuntu cannot boot because it cannot find on this partition the the file: 06." [/FONT]

Any ideas?  (I went ahead and installed regular ubuntu on top of it, but am wondering what I might have done wrong for the next time I try it.)

Did you install Ubuntu on a test hard drive with another OS active?

It's possible that your Grub "menu.lst" file points to the wrong hard drive.

As an example, I have an "expendable" removable USB hard drive with Ubuntu on it for testing.

When I installed it, I had to install GRUB on "(hd2)" because it was the third hard drive in my system (the first 2 are Windows drives).

Anyway, when I do a USB boot, the Ubuntu drive is logged in as the FIRST drive.

Therefore the part of "menu.lst" that contained "root=(hd2,0)" had to be changed to "root=(hd0,0)".

How to get in in the first place to edit the file?

Easy... during boot (at the grub screen, before it starts loading), hit "E" for edit. Hit "E" again to edit the first line. Change "(hdx,0)" to something different (try (hd0,0), (hd1,0), etc...) until you find one that works.

Then after you get in, fix /boot/grub/menu/lst by editing it and make the fix permanent.

Good luck.

-- Roger

---

