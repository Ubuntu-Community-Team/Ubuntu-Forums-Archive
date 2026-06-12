---
title: "In a bit of a mess with Ubuntu Studio and Unity"
date: 2013-05-17
forum: Ubuntu Studio
---

### Post by b9k9kiwi on 2013-05-17
Not a mess really and, anyway, this is on my No.2 (non-mission critical) PC.

I initially had Ubuntu installed (via WUBI) on drive D, with Win7 on drive C.  I then installed Ubuntu Studio (non-WUBI, CD install), expecting it to be installed alongside Ubuntu on drive D - but it installed alongside Win7 on drive C.

No matter, there's plenty of room on drive C and, as I didn't need the original Ubuntu install, I uninstalled from Win7 giving me back the whole of drive D.

I'm not sure I want to have things this way in the long term, so I may uninstall Ubuntu Studio and reinstall it to drive D - I guess I will have to use WUBI to make sure that is what happens.

The main issue is that I have installed Unity (which I really like) in Ubuntu Studio, but I can't get it to boot to the Unity desktop.  The GRUB menu doesn't offer me any desktop options and I can't find any settings dialogue to give Unity to me.  I installed Unit from the software centre and, when that didn't work, I did apt-get install etc.

So, what is the best strategy for uninstalling and reinstalling Ubuntu Studio on a Win7 PC, and how do I bring up Unity as the preferred desktop.

Some help would be appreciated.

---

### Post by zequence on 2013-05-20
Using Wubi is not the recommended method to install, as it makes reading from disk very much slower - just a tip.

You don't choose desktop at the GRUB menu. You do that at the login menu. Probably you now have the Ubuntu lightdm menu. Click the button in the login area. It has the Circle of Friends symbol (the Ubuntu symbol). You'll see some selections there.

---

### Post by b9k9kiwi on 2013-05-20
Thank you for your reply zequence.

Other sources (including the Ubuntu Studio site) tell me that Unity in Ubuntu Studio is either not possble, or too much trouble to be worth it.

In the end, it wasn't worth the heartache, so I booted Win7 from CD and zapped the Ubuntu Studio install.  I have now installed the standard Ubuntu 13.04 on D drive (non-WUBI of course), installed Jack and Ardour, configured RT audio and it all works okay and with Unity as I wanted.

Mind you, I now have the recursive error/needs a reboot problem (it takes 2 or 3 attempts to actually get Ubuntu up and running), but that is another story.

---

### Post by zequence on 2013-05-21
There's no conflict between Ubuntu Studio and Unity. It's just that Ubuntu Studio has decided to use XFCE as the default DE, as it is easier on the hardware, and back when Unity was new, it was the safest bet. 
You may install one or the other on top of each other. The big benefit with installing Ubuntu Studio though is getting stuff preconfigured, and apps preinstalled. But, you can still find all the ubuntustudio meta packages in the main repo. Just do: 

```
apt-get search ubuntustudio
```

---

### Post by b9k9kiwi on 2013-05-22
Okay, thanks again.

I have ardour and Qjackctl working nicely, which is actually all I need  ... but I might do the ubuntustudio packages later to see what is there I might find useful.

---

