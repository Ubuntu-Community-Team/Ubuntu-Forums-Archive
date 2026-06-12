---
title: "Resolution issue since kernel 3.4"
date: 2012-06-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by DingusFett on 2012-06-17
Hi guys, I'm currently running Ubuntu 12.04 and have been having issues since following the steps [here]("http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads") to upgrade to 3.4 kernel. I was stuck at the best resolution I can get is 1024x768. I was able to install drivers and in the X server settings I managed to get the resolution to 1152x864, however prior to the upgrade I was running 1440x900.

After messing around with various google results, I got no closer so I gave up and wiped the partition and reinstalled 12.04 with the 3.2 kernel, only to have the same issue. The graphics card is an MSI8600GT-T2D256E-OC (what it says on the card that I could see), I have also tried running on-board graphics but could again only get 1024x768. Figuring something went wrong installing, I have again tried the wipe and reinstall method, to no avail. I have just booted into the Windows partition and had the same issue of only being able to get to 1024x768.

I have tried using both driver options in the Additional Drivers section, and through the x-swat ppa as suggested by one google result, as well as another monitor that should run ~1280x1024 but this also didn't pick up the right resolutions. The Ubuntu install is 12.04 64-bit, and the Windows install is Win7Pro 32-bit. Have absolutely no idea where to go from here to try to resolve this. From what I can gather, the card is not reading the information off the monitors, as they also appear as Laptop in the Displays screen.

---

### Post by dino99 on 2012-06-17
be sure to remove xorg.conf if it exist

sudo rm /etc/X11/xorg.conf

then reboot

---

### Post by DingusFett on 2012-06-17
Thought tried that before but gave it a shot anyway, and my resolution was reset back to 1024x768. Again could only change up to 1152x864 through X server settings.

---

### Post by jerrylamos on 2012-06-17
Which VGA adapter are you using?  I'm O.K. on a couple ATI adapters, 

another ATI is having fits with the FGLRX driver so I set resolution with command line xrandr. Sort of works, example wallpaper has an overlap, and "full screen" isn't but I can stretch the screen to fit mostly.
 
That's a widescreen notebook with problems on both the laptop and the external screen.  Systems settings displays gets a segfault on selecting "apply".  There's a bug written with some developer activity. bug #1007588 I think.

Do note in the forums that NVIDIA (however you spell that) is having problems also.

I do get 1440x900 with ATI radeon xpress 200 no problems now, I did have to use nomodeset to boot the startup USB disk.  Yesterday booted O.K. without nomodeset.

Jerry

---

### Post by DingusFett on 2012-06-17
Yeah, I have noticed the problems others have had with NVidia. It's odd that it worked perfectly until the kernel upgrade, then since then it's been broken, even with wiping it and going back to the older kernel, and same issue in Windows.

---

### Post by DingusFett on 2012-06-18
If this helps, it seems that since changing to kernel 3.4 the graphics card isn't reading the EDID from the monitors. Any ideas?

---

### Post by DingusFett on 2012-06-18
As an update, just tried using the 302.17 Nvidia drivers from the X-swat PPA and still have the same issue.

---

### Post by dino99 on 2012-06-18
> **DingusFett said:**
> As an update, just tried using the 302.17 Nvidia drivers from the X-swat PPA and still have the same issue.

if you get the same issue on both linux & windows, then the trouble is with the hardware. Is it plugged via vga/hdmi/? Watch the display doc.

---

### Post by jerrylamos on 2012-06-18
Saw there was a fix released for my screen resolution problem see bug #1007588.  Just updated 12 noon EST 18 June and display resolution fixed, Systems Settings Display finally works with no segfault.

Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
on widescreen notebook with external monitor.

Now there's one funny, pull down menus like the top right applet have a white stripe with black lettering.  Must be some default changed I don't know where.

Anyway, try today's update & see if your screen resolution is affected....

Jerry

---

### Post by balloons on 2012-06-18
> **dino99 said:**
> if you get the same issue on both linux & windows, then the trouble is with the hardware. Is it plugged via vga/hdmi/? Watch the display doc.

I agree this sounds very much like something changed on the hardware side. If reinstalling 12.04 didn't work, windows doesn't work and both of them "used to" something non-software has changed.

---

### Post by philinux on 2012-06-18
> **jerrylamos said:**
> 

Now there's one funny, pull down menus like the top right applet have a white stripe with black lettering.  Must be some default changed I don't know where.



Jerry

Menus borked here too. I think there was a gtk or nautilus update today.

---

### Post by jerrylamos on 2012-06-18
> **philinux said:**
> Menus borked here too. I think there was a gtk or nautilus update today.

In the bug #1007588 there was discussion of a gtk fix just released earlier today ....

Jerry

---

### Post by DingusFett on 2012-06-19
Thanks, I will run updates when I get home from work and see how it goes. 

I agree that in theory seems like a hardware issue, but it is very odd that it only happened after upgrading to kernel 3.4; The graphics card only has DVI-D output, but I lack a cable, so currently has VGA cable from monitor, to VGA->DVI-D adapter on the graphics card. I haven't had issues with this before, but if it persists after updates tonight I will try to get a DVI cable to try and if not will look at getting a new card.

---

### Post by philinux on 2012-06-19
> **jerrylamos said:**
> In the bug #1007588 there was discussion of a gtk fix just released earlier today ....

Jerry

Just updated and unity --replace has fixed this.

---

### Post by philinux on 2012-06-19
Oh eck. Try the network and messaging dropdown.

---

### Post by jerrylamos on 2012-06-19
> **philinux said:**
> Oh eck. Try the network and messaging dropdown.
network drop down has 12 lines.  The first three are black on white, readable.  The next none are light grey on white, not readable unless the cursor is passed over them.

Jerry

---

### Post by kevpan815 on 2012-06-20
> **DingusFett said:**
> Hi guys, I'm currently running Ubuntu 12.04 and have been having issues since following the steps [here]("http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads") to upgrade to 3.4 kernel. I was stuck at the best resolution I can get is 1024x768. I was able to install drivers and in the X server settings I managed to get the resolution to 1152x864, however prior to the upgrade I was running 1440x900.

After messing around with various google results, I got no closer so I gave up and wiped the partition and reinstalled 12.04 with the 3.2 kernel, only to have the same issue. The graphics card is an MSI8600GT-T2D256E-OC (what it says on the card that I could see), I have also tried running on-board graphics but could again only get 1024x768. Figuring something went wrong installing, I have again tried the wipe and reinstall method, to no avail. I have just booted into the Windows partition and had the same issue of only being able to get to 1024x768.

I have tried using both driver options in the Additional Drivers section, and through the x-swat ppa as suggested by one google result, as well as another monitor that should run ~1280x1024 but this also didn't pick up the right resolutions. The Ubuntu install is 12.04 64-bit, and the Windows install is Win7Pro 32-bit. Have absolutely no idea where to go from here to try to resolve this. From what I can gather, the card is not reading the information off the monitors, as they also appear as Laptop in the Displays screen.

No problems here with 3.5.0-999 displaying 1366x768 on both my 19 and 20 inch Vizio HDTV's. Just FYI.

---

### Post by philinux on 2012-06-20
> **jerrylamos said:**
> network drop down has 12 lines.  The first three are black on white, readable.  The next none are light grey on white, not readable unless the cursor is passed over them.

Jerry

Righto. All fixed with recent update.

[edit] not just reoccurred. Had to use unity --replace to restore proper menus.

---

### Post by kevpan815 on 2012-06-20
> **kevpan815 said:**
> No problems here with 3.5.0-999 displaying 1366x768 on both my 19 and 20 inch Vizio HDTV's. Just FYI.

Correction:: My 19 inch Vizio uses 1360x768 and my 20 inch uses 1366x768, both are the Default Resolution for those HDTV's with HDMI, however.

---

### Post by DingusFett on 2012-06-21
Well, I got home from work tonight, and my problem has resolved itself. Haven't had a chance to go grab a DVI-D cable or graphics card yet, but everything is now fine.

---

