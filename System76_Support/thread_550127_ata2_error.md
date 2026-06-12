---
title: "ata2 error"
date: 2007-09-13
forum: System76 Support
---

### Post by ncappel1 on 2007-09-13
Help! earlier I tried to log off my user name. after I clicked the logout button nothing happened. The desktop froze. the mouse was still functional, as was the keyboard. I thought there may have been some memory hog, so I alt+crtl+F1 into a terminal (the other terminal wouldn't respond) to see "top" but nothing was out of the ordinary. there were console messages being displayed that said: ata2:port failed to respond. 30 secs, status 0xd0).

I tried searching the forums and google for some answers, (I launched firefox from the keyboard button) and I read that the error message could be caused by many things, but that primarily they were kernal related.

I should have saved my messages from dmesg, but I didn't think of it. I tried to shut down from the command line, but nothing would respond. I finally powered off by pressing the power button for 5 secs. when I rebooted everything seemed normal. I checked dmesg to see if the errors were still there. I see way at the bottom that the same messages (as far as I can tell) are being repeated regarding ata2. is this a serious problem? should I be concerned? Im hesitant to try fixes when I don't know what the exact problem is. any help would be apreciated. 

specs:
uname -a: Linux ubuntu 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
Gazelle performance gazv3
2.0 GHz Intel Core 2 duo
2 x 1 GB DDR2 667 MHZ
nVidia GeForce 7300 FX

---

### Post by thomasaaron on 2007-09-13
First, make sure you do not have a cd in the drive while it is not being used. Also run your System 76 driver. This should provide immediate relief if you have not already followed the instructions on this bug report: [https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

Once you have done that, you should be able to follow the firmware update instrcutions.

It was originally for the darter, but was later extended to the gazelle value. Instructions are near the bottom of the thread.

---

### Post by ncappel1 on 2007-09-13
just to clarify, "Run the driver" means install the driver from the window, or "restore system?"

also, i double checked, there has been no cd in my drive for several days. :)

---

### Post by thomasaaron on 2007-09-14
System > Administration > System 76 Driver
Install Driver Tab > Install Button

---

