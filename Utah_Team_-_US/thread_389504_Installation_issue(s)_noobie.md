---
title: "Installation issue(s) noobie"
date: 2007-03-20
forum: Utah Team - US
---

### Post by nfll on 2007-03-20
Hello,  new to Linux/ubuntu and have encountered an issue with the CD operation of the program vs installing on my computer(Burned own copy of CD).
Computer: Win 2000 Pro, P4 2.4 ghz , 2 gig RAM, Matrox P650 (2D) video card/Diamondtron Fe2111sb Monitor.
I am attempting to operate Ubantu from the CD, not yet ready for install on my computer.
What happens at boot up:  Seems to be a problem with the GUI elements, card/resolution of monitor etc.  Monitor screen goes dark and colored pixels appear across the horiz. center of the screen. (No Ubantu logo discernable).  Eventually a walnut colored screen appears, but nothing, again, is discernable, possibly the desktop?
I tried the CD operation on another computer with a different graphics setup and have had no problems in that regard, so the CD itself appears to be working correctly (did a CD check to be sure).  Boots and loads and arrives at a proper desktop on that machine.
On the first machine I have set the resolution to 1024 x 768 via Windows in hopes that might accomplish something,-no luck.  Can't find any resources that specifically address Matrox cards or my monitor so am hoping there is a solution?  Thanks.

---

### Post by nfll on 2007-03-20
OP:   After further experimentation I have been able to access and see the setup screen(ctl+alt+1) and F6 , I believe, changed  to the various display resolutions, CD continues to then boot and I can at last see the loading screen, but when it gets to the desktop it is non discernable.  Will continue with experimentations.  Awaiting rescue.

---

### Post by stuporglue on 2007-03-20
nfll, 

You may want to try the alternative install CD. It uses a text-based installer instead of the graphics. When it is done, you reboot and have a normal Ubuntu desktop (ie. after the install, you'll have graphics). 

I've had some setups where the graphical installer didn't work very well, but the text-based installer worked fine. 

Hope that helps, 
Stuporglue

---

### Post by nfll on 2007-03-21
Thanks for the information.
  I have a question(s) about "installation".  When/if I used the alternate CD for installation is ubuntu then installed ON my computer requiring the various disk partitioning process etc to be performed etc. or if I were to get the Live CD install to work, I'm assuming to use ubuntu (live CD version) still eventually require disk partitioning as well?  I haven't quite got my mind around how the install(s) will function quite yet.  The reason I'm asking is at this point I don't want a full system install until I look at how it all comes together, unless of course the full install being the best way to see the program at its best?  I understand the difference in system operation speed using the Live the CD.

---

### Post by stuporglue on 2007-03-21
>  I have a question(s) about "installation". When/if I used the alternate CD for installation is ubuntu then installed ON my computer requiring the various disk partitioning process etc to be performed etc.


Yes, the alternative install CD is essentially just an installer. There is no live graphical desktop option with it. The install process does require partitioning.

>  I'm assuming to use ubuntu (live CD version) still eventually require disk partitioning as well? I haven't quite got my mind around how the install(s) will function quite yet. 

The Live CD is two things in one. It is a Live Linux environment that for many users allows the user to get a feel for how the system will function on their computer. When used in this way, no partitioning is required. 

While in the Live Linux environment, there is an icon that you can double click which starts an installer. If you use this installer, then partitioning is required. 

>  The reason I'm asking is at this point I don't want a full system install until I look at how it all comes together, unless of course the full install being the best way to see the program at its best? I understand the difference in system operation speed using the Live the CD.

Sorry about that. I just assumed you were installing. :-) 

A full install is the *BEST* way to see how Linux works. The Live CD isn't always able to detect the graphics correctly (ie. sounds like your case), but the full installer usually does. Also, the Live CD doesn't ship with the proprietary NVidia or ATI drivers, or proprietary wireless drivers, all of which can be configured on an installed system. 

That said, using a Live CD first is a good way to get a feel for the system so you can decide before partitioning and installing. 

I might check the md5sum of the CD you burned. If it's incorrect (ie. the CD is corrupt) you could try redownloading and burning a new CD before taking the full install route.

If the Live CD isn't detecting your graphics correctly, the only way for you to experience Ubuntu may be to do an install.

---

### Post by GTropic on 2007-03-22
I have had many problems with Ubuntu and Matrox video cards.  Do you have a different video card that you could install?  My experience is that Ubuntu does not work well with Matrox video cards.

GT

---

### Post by nfll on 2007-03-22
I need the Matrox card for graphics programs (best card for that purpose).  I don't do gaming so the 3d cards would not improve /help my situation graphics wise.

---

