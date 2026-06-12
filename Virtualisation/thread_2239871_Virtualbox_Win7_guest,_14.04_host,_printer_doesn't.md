---
title: "Virtualbox Win7 guest, 14.04 host, printer doesn't work"
date: 2014-08-16
forum: Virtualisation
---

### Post by sgofferj on 2014-08-16
Hi,

I have installed Win7 in a VirtualBox and am trying to install my Canon LBP-5050 printer. Trouble is, Win7 reports that the device has malfunctioned and was deactivated. On the same host, in a WinXP guest, the printer works. Also, on a Win8 laptop, it works. Is there anything with Win7 and USB in Virtualbox that I need to consider additionally? I tried a few other devices, e.g. a bluetooth stick and those worked.

-S

---

### Post by TheFu on 2014-08-16
USB for a printer inside a VM?  Why?

I'd setup the printer on the Linux hostOS and use it as a print server. Much easier, plus it will work for portable device printing too. [https://help.ubuntu.com/12.04/serverguide/cups.html](https://help.ubuntu.com/12.04/serverguide/cups.html) you can even setup samba with it to let printer drivers for Windows automatically install.

---

### Post by sgofferj on 2014-08-17
Because the LBP-5050 doesn't seem to work with 14.04. Gutenprint has no driver and the Canon drivers don't work. I'd love to have this printer running at the server in the kitchen instead of the living room because it's huge... But doesn't work.

---

### Post by TheFu on 2014-08-17
> **sgofferj said:**
> Because the LBP-5050 doesn't seem to work with 14.04. Gutenprint has no driver and the Canon drivers don't work. I'd love to have this printer running at the server in the kitchen instead of the living room because it's huge... But doesn't work.

Understood. That sucks.
Is [https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=CanonCaptPrinterDriver#Ubuntu_13.10_Install](https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=CanonCaptPrinterDriver#Ubuntu_13.10_Install)
what you tried? Where was the failure?

I expect my printer(s) and scanner to stop working with 14.04 too. They aren't Canon. If necessary, I'll setup a tiny, tiny, 1204 VM to be the network print server with 256MB of RAM and no GUI. We don't print much at all, but scanning needs to work a few times a month over the network.

---

### Post by JKyleOKC on 2014-08-18
> **TheFu said:**
> I expect my printer(s) and scanner to stop working with 14.04 too. They aren't Canon. If necessary, I'll setup a tiny, tiny, 1204 VM to be the network print server with 256MB of RAM and no GUI. We don't print much at all, but scanning needs to work a few times a month over the network.I just posted a similar suggestion on another thread as a possible solution for getting a Lexmark printer to work, although I suggested a WinXP VM isolated from the web but available on the LAN, as a way to use the Windows drivers and still get the printer to work for all the Linux installations...

Do great minds think alike? :lolflag:

---

### Post by fidelis2 on 2014-08-28
... I could solve the Win7 guest's USB printer problem by using a WinXP guest. Please see here for full story:
[http://ubuntuforums.org/showthread.php?t=2239914&page=2&p=13110116#post13110116](http://ubuntuforums.org/showthread.php?t=2239914&page=2&p=13110116#post13110116)

---

### Post by pdc on 2014-08-28
sgofferj has a distinguished CV on his post; I acknowledge all that; 

the LBP5050 should work fine on a 32bit ubuntu; with the 64bit, Canon document various extra files that need to be installed in their extensive readme.txt

> sudo apt-get install libglade2 libpopt0:i386 ia32-libs

simplest is to accept a 32bit system; it may for some be a choice between 32bit and working printer; the issues seem to be with cutting edge distros: Fedora and Ubuntu; 

the LBP5050 uses the CNCUPSLBP5050CAPTK.ppd

---

