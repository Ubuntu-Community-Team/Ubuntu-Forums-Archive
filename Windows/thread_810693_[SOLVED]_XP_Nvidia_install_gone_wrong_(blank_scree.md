---
title: "[SOLVED] XP Nvidia install gone wrong (blank screen)"
date: 2008-05-28
forum: Windows
---

### Post by DirtDawg on 2008-05-28
I got a new Nvidia PCI card (e-Geforce 6200) that installed without a hitch on Ubuntu, but I have run into serious problems with my Windows XP partition.

I turned off the computer, installed the card, and rebooted. The screen resolution was very poor, but I expected that.

I then used the driver disc to install the drivers. Everything went as expected, but when I hit the final "install" button, the computer asked if I was sure I wanted to install the drivers as they could seriously damage my system. I hit the continue button (who knows what Windows warnings to take seriously?) and the screen went blank, totally blacked out. I waited, but nothing happened. 

Upon reboot, after the windows logo/startup screen, the screen went black again. 

The PCI card is a replacement for an onboard intel card. I attempted to plug the monitor input into the intel card, but no dice. I'm guessing Ubuntu disabled the onboard card. I looked at the BIOS, but I am not familiar enough with BIOS to figure out where the Intel card is (de)activated.

I got my computer through Dell several years ago and they gave me 4 discs with it. One had the XP operating system, but it says it is a reinstallation CD and says nothing about safemode. I hesitate to use the reinstallation disc because I know Winodows has a tendency to overwrite GRUB and if Ubuntu became inaccessible, I would really be up a certain, filthy creek.

After some tinkering I have managed to mount my Windows partition, but it is read only.

Any help would be appreciated. I have googled, but it's clear the Windows community is much less likely to help each other out in a pinch.

Thanks.

---

### Post by fwre01 on 2008-05-28
Have you tried taking the PCI card out? this should enable (if it has been disabled) the original card

normally instead of disabling the card it works through them in order at boot time

---

### Post by smoker on 2008-05-28
if you can boot into safe mode (tap the f8 key as soon as the bios screen disappears and before windows begins to load proper). once in safe mode, go to add/remove programmes and uninstall the nvidia drivers. you should hopefully now be able to boot into normal windows as before, albeit, without the proper graphics drivers. don't use the disk again, but go to nvidia support site and download the latest drivers for your card, and try installing these.

also, point to note, does your graphics card need a power source, some do, if so make sure it is connected.

best of luck

---

### Post by DirtDawg on 2008-05-28
> **smoker said:**
> if you can boot into safe mode (tap the f8 key as soon as the bios screen disappears and before windows begins to load proper). once in safe mode, go to add/remove programmes and uninstall the nvidia drivers. you should hopefully now be able to boot into normal windows as before, albeit, without the proper graphics drivers. don't use the disk again, but go to nvidia support site and download the latest drivers for your card, and try installing these.

also, point to note, does your graphics card need a power source, some do, if so make sure it is connected.

best of luck

Ah, thank you. I will try that. I thought I would need a safemode disk to boot up. If this doesn't work, I will try uninstalling the card as suggested. (Now that I think about it, I have a norton AV disc that I think i might be able to use as well).

Thanks to both of you. I will post the results.

Ironic that people grumble about Linux not being ready for the average user, but it's the one that "just works". Of course, Ubuntu users already know that :)

---

### Post by fwre01 on 2008-05-28
Its funny becasue a nvidia card was what tipped me over the edge when i first changed to linux.

i bort a spanking new nvidia card and cudnt for the life of me get it to work in XP, i booted feisty and it worked almost out of the box, and at that point i blew XP away and have learnt so much since doing so.

---

### Post by DirtDawg on 2008-05-28
That worked great! It turns out the problem was that I did not deactivate the onboard card before installing the drivers. Kind of an obvious thing in hindsight. 

### For others with similar problems ###
* First I booted into safe mode with F8 as suggested. Then right-clicked My Computer and chose Manage. Under the Display Drivers, I right-clicked and chose Uninstall.
* After reboot, I logged in as usual, right-clicked My Computer and chose Manage, then Display Devices again. Then I right-clicked on my onboard card and chose Disable Device and clicked Yes when it asked me if I was sure (don't worry, VGA mode does not require the onboard card to be enabled).
* Finally, I installed the driver I had downloaded from the Nvidia site. The computer rebooted and everything worked fine.

Thanks again for the help :KS

EDIT: I figured out the onboard card was the problem by, get this, reading the manual! If you are having similar issues, I would recommend doing the same before blindly imitating the above steps.

---

### Post by DirtDawg on 2008-05-28
> **fwre01 said:**
> Its funny becasue a nvidia card was what tipped me over the edge when i first changed to linux.

i bort a spanking new nvidia card and cudnt for the life of me get it to work in XP, i booted feisty and it worked almost out of the box, and at that point i blew XP away and have learnt so much since doing so.

Well at least XP is good for something :D

---

### Post by SunnyRabbiera on 2008-05-28
> **fwre01 said:**
> Its funny becasue a nvidia card was what tipped me over the edge when i first changed to linux.

i bort a spanking new nvidia card and cudnt for the life of me get it to work in XP, i booted feisty and it worked almost out of the box, and at that point i blew XP away and have learnt so much since doing so.

well thats how it is though with Nvidia and ATI cards, even with XP being more "out of the box" as people say sometimes linux can best it even with the ATI cards causing so much havoc sometimes people get lucky with them

---

### Post by smoker on 2008-05-28
glad you got it sorted, xp is fine when you get it preinstalled and with a driver disk. but once you start changing the hardware, that's when it's not so user friendly!

---

### Post by r76 on 2008-05-29
> **smoker said:**
> glad you got it sorted, xp is fine when you get it preinstalled and with a driver disk. but once you start changing the hardware, that's when it's not so user friendly!

So the moral of the story is Windows is fine "out-of-the-box", but don't for God's sake put anything IN the box!?! :p

---

