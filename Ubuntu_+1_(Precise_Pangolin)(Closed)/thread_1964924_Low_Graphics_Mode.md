---
title: "Low Graphics Mode"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Zukaro on 2012-04-24
I need help; I've put the Ubuntu 12.04 ISO on a CD and tried to install it on my PC.  12.04 works from USB on my netbook (Acer Aspire One ZG5/AOA150), but on my PC (custom made, will put specs at bottom of post) after installing it when I go to boot up for the first time it tells me it's boot into low graphics mode, at which point I can't do anything else (sometimes the mouse is there but usually it just freezes completely at that message).

Can anyone help me with this?  I've also tried to install Ubuntu 11.10 with no luck (after telling it if I want to install alongside Windows etc it tells me it was unable to mount the partition (something like that)).  That was without Windows 7 on (I tried with Windows 7 also (for Ubuntu 12.04, didn't try with 11.10) and same problem (low graphics mode)).

Specs:
Motherboard: Asus P7P55D PRO
CPU: Intel Core i5 760 @ 2.80GHz
RAM: 4GB
GPU: NVIDIA GeForce GTX 460

---

### Post by zombifier25 on 2012-04-25
Hmm try installing Nvidia's proprietary drivers and see that help. Click the Ubuntu icon on the Launcher and search for "restricted drivers".

---

### Post by Peter09 on 2012-04-25
How old is the image - Pangolin is still Beta and subject to lots of bug fixes. Ensure you downloaded the have the latest. I know that during the development phase there were issues with the NVidia driver - I'm not sure if they have been resolved yet. I think people are being advised to not install the proprietary driver.

---

### Post by Zukaro on 2012-04-25
Okay; I'll just wait for the official release and then try again.  If the same thing happens I'll ask here again (in this same thread).

(will also try the proprietary NVIDIA drivers on the official release if it still doesn't work)

With the drivers would I install them during installation? (as when Ubuntu is in low graphics mode I can't do anything at all (most of the time the mouse doesn't even appear and the system freezes)).  And if I install them during installation do I need to save them to my hard drive/removable media (I'm guessing I'd have to since the changes wouldn't be saved to the CD)?



As for how old the image I'm using is, it's a few weeks old, I don't know how old exactly but probably closer to a month old.

---

### Post by Peter09 on 2012-04-25
Well a month is far too old, remeber this is beta software, a month ago is a long time, there have been lots of bug fixes since then.
 
If you can get to a terminal then you could do:
 
```
 
sudo apt-get update

```
 
and then
 
```
 
sudo apt-get upgrade

```
 
with luck it could get you to the latest versions of every thing..Reboot and see what happens :)

---

### Post by Zukaro on 2012-04-25
If I need to get into the terminal upon booting from the hard drive I can't.  The live CD runs fine but as soon as I go to boot up it ends up in low graphics mode and freezes.  I'll probably just wait till tomorrow and burn a new CD though (I need to finish installing all my games in Windows then do a backup anyways :P).

However, older versions of Ubuntu didn't work either (I only tried 11.10 though).  It told me something about being unable to mount to the hard drive (that didn't happen when trying to install 12.04 however).  So when it's been officially released I'll see if I can get it working.  :P

---

### Post by Peter09 on 2012-04-25
Hold down the shift key while its booting, should get you to recovery mode. In the menu select root prompt with networking (think thats what its called) you can issue the commands from there.

---

### Post by Zukaro on 2012-04-25
Okay, thanks.  :)

Edit:
It works now; just needed to use the 64bit version.

---

