---
title: "Ubuntu 12.04 Beta 2"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Rjames426 on 2012-04-01
Hey guys im trying to install Ubuntu 12.04 beta 2 on my old Dell Inspiron 8600. I downloaded the x86/i386 version and went to install it and got the famous error saying the CPU is not compatible with that version... so i downloaded the x64 bit version (just to try) and got the same... REdownloaded the X32 bit version and still cant get it working. can someone help me out? Is my computer just to old? heres my specs.

CPU: intel pentium M
RAM: 512mb
HHD: 40gb

Note: It runs windows XP and I have Ubuntu 10.04 installed before too.

---

### Post by oldos2er on 2012-04-01
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by Rodney9 on 2012-04-01
You should try Xubuntu 12.04 

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

or Lubuntu 12.04

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Rodney

---

### Post by grahammechanical on 2012-04-01
The reason is that no longer do we get a non-pae kernel in Ubuntu, whether 32bit or 64bit. But Xubuntu does have a non-pae kernel by default. So, that will load. It will no doubt be better for that machine anyway.

Your CPU cannot work with a pae enabled kernel.

Regards.

---

### Post by BertN45 on 2012-04-02
+1 

Afterwards you could always install the Ubuntu desktop, but given your memory size, I would try the 2D desktop. 
I run it on an AMD 3200+ with also 512 MB.

Before installing the desktop you have to update your system, since there seems to be a bug that prevents you to install the Ubuntu desktop.

---

### Post by RJARRRPCGP on 2012-04-02
Do not get 64-bit! Because 64-bit don't exist in Pentium M! (or disabled by Intel at factory)

---

### Post by jerrylamos on 2012-04-02
Lubuntu 12.04 generic (no pae) runs FINE on my Pentium M Thinkpad T40.

So you've got a couple choices, lubuntu or xubuntu.

Note, lubuntu comes with chromium internet browser.  Start synaptic, removing chromium installs Firefox automatically.  Then install adobe-flashplugin, load in my couple hundred bookmarks, and away I go.  Easy.

If I'm doing much copying of internet articles I load libreoffice.  abiword is a bit too simple (minded) for me.

Easy to add applets to the bottom panel, and a LOT faster to start them than the Unity launcher.  And my own wallpaper my wife on vacation in Australia on a gorgeous beach.

If you're really a masochist I suppose you could try loading Unity-2D which will run on generic.

Oh, lubuntu still fits on a CD although I usually just boot the .iso image from the hard drive.

[http://cdimage.ubuntu.com/cdimage/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/cdimage/lubuntu/daily-live/current/)

Enjoy.  

Jerry

---

### Post by jbicha on 2012-04-02
Ubuntu 12.04 fits on a CD too. Perhaps it won't for 12.10 though.

---

