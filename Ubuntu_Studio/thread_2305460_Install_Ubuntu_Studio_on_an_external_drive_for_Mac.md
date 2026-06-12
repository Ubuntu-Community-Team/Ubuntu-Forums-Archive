---
title: "Install Ubuntu Studio on an external drive for Mac"
date: 2015-12-06
forum: Ubuntu Studio
---

### Post by Music_Guy on 2015-12-06
I'd like to install Ubuntu Studio on an external drive for use with a Macbook Air, for my daughter. If possible, I would like to install it from my iMac, and give her the drive to use. I don't know that I would necessarily need dual boot, since I was thinking that I could show her how to change the startup drive when she wants to use Studio. Also, she probably won't need the audio portions - just the photo and video. Can someone explain (or point me to a post) that describes how to do this? Thanks.

---

### Post by CrocoDuck on 2015-12-06
Hi There! I never tried to run Linux in Mac, but your question reminds me of [a guide I stumbled across some time ago]("https://www.linux.com/learn/tutorials/718439-how-to-run-fedora-linux-on-the-macbook-air-without-touching-the-ssd"). It is for Fedora, but chances are it will work with Ubuntu as well. Have a look at [this section]("http://ubuntuforums.org/forumdisplay.php?f=328") of the forums as well and, of course, google a lot and save your data before trying anything.

---

### Post by Bucky Ball on 2015-12-06
Easier option to my mind. Install Xubuntu (Ubuntu Studio uses a lot of it and xfce4 for a desktop environment) then install:

ubuntustudio-photography 
[A collection of applications forming a photograph touchup and editing suite]

ubuntustudio-graphics 
[A collection of applications aimed at 2D/3D creation and editing]

ubuntustudio-video
[A collection of applications aimed at video creation and editing]

Have a look around in Synaptics for any other UStudio 'bundles' you might need and you'll end up with a custom spin for a photo/vid enthusiat (which may be further tweaked to their liking). Wrap it up with a ribbon and job done! 

Installing a full Ubuntu Studio and then wheedling out the dross and redundancy for your purposes may prove problematic and time consuming ...

PS: You probably already know one way or the other, but far as I know, Ubuntu can only be installed on Mac via disk, not USB. At least iMacs ...

PPS: You could go one step further, which is the route I would take but I have a mini fetish, and install the minimal and then add xfce4, the few other things you need for day to day, then the UStudio bundles above.

---

### Post by Music_Guy on 2015-12-09
Hi CrocoDuck, I tried to follow what you suggested for Fedora. I did not use livesub_creator, since I don't have any windows machines. And, I installed Ubuntu Studio on an external hard drive using my Ubuntu machine. When I tested it, my iMac could not even see the external drive. I'll look into liveusb-creator - maybe that's the key.

Bucky Ball - if I understand you correctly, you are suggesting that I load Xubuntu and the rest onto the macbook air. Is this correct? The biggest problem with that approach is that the MAB has very limited hard disk space - 250Gb if I remember. A lot of that is taken up by the OSX.

Thank you both for your suggestions. I'll keep plugging away.

---

