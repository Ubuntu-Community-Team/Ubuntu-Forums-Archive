---
title: "VirtualBox or VMWarePlayer ?"
date: 2011-02-26
forum: Virtualisation
---

### Post by hoboy on 2011-02-26
I need a virtualbox to use on ubuntu.
VirtualBox OSE and VMWarePlayer are the only one I have heard of.
witch one has the larger screen ? or are there others then these 2 ?

---

### Post by killfall on 2011-02-26
Personally I would say virtualbox ose. Its great to use. Free. Easy to set up. Screen res can be anything you like, you aren't limited. It's my favorite by a long shot.

---

### Post by hoboy on 2011-02-26
> **killfall said:**
> Personally I would say virtualbox ose. Its great to use. Free. Easy to set up. Screen res can be anything you like, you aren't limited. It's my favorite by a long shot.

Thanks, what do you mean by Screen res ?
I have just installed virtualBox and installed win7 because I do visualStudio programming and monodevelop is not yet like vs2010 in my opinion, but I tough that the screen was a bit small.

---

### Post by doas777 on 2011-02-26
well, both are good software. VMware has better 3da but it costs a little. you can of course use VMWare Player for free, but the workstation package was the only one that would run some of my games (galciv2). 

other than games, I use VBox much more, since it is free, and does work nicely. the seamless mode is a most excellent enhancement to my daily computing. two OSes on the same desktop (on a dual head rig). dream come true.

no idea what you are asking about screen size. the VMs internal res depends on your virtual vidcard driver, and the external res can be fullscreened to whatever size your monitor is. just be sure to install the client tools for whatever platform you choose so you get a good driver and good internal resolution.

---

### Post by hoboy on 2011-02-26
> **doas777 said:**
> well, both are good software. VMware has better 3da but it costs a little. you can of course use VMWare Player for free, but the workstation package was the only one that would run some of my games (galciv2). 

other than games, I use VBox much more, since it is free, and does work nicely. the seamless mode is a most excellent enhancement to my daily computing. two OSes on the same desktop (on a dual head rig). dream come true.

no idea what you are asking about screen size. the VMs internal res depends on your virtual vidcard driver, and the external res can be fullscreened to whatever size your monitor is. just be sure to install the client tools for whatever platform you choose so you get a good driver and good internal resolution.
I have installed vindows 7 in the virutalBox.
how do I install the client tools for that ?

---

### Post by doas777 on 2011-02-26
> **hoboy said:**
> I have installed vindows 7 in the virutalBox.
how do I install the client tools for that ?
yup. in the VBox window, go to Devices -> Install guest Additions
it will mount a virtual CD to your Win7 optical drive, so autorun the disk, and it will walk you through the tools install.

after that, once everything is installed and you have rebooted, rclick your desktop and select "Screen Resolution" to adjust the size of the window. the resolution must be less than or equal to the resolution of the host PC. if you want to use fullscreen or seamless mode, I recommend setting the res equal to the hosts screen res.

just a note, every time you upgrade VBox, you will have to reinstall the client tools. not a big deal. if you virtualize a linux OS as guest, you will also have to reinstall them after kernel upgrades.

---

### Post by hoboy on 2011-02-26
> **doas777 said:**
> yup. in the VBox window, go to Devices -> Install guest Additions
it will mount a virtual CD to your Win7 optical drive, so autorun the disk, and it will walk you through the tools install.

after that, once everything is installed and you have rebooted, rclick your desktop and select "Screen Resolution" to adjust the size of the window. the resolution must be less than or equal to the resolution of the host PC. if you want to use fullscreen or seamless mode, I recommend setting the res equal to the hosts screen res.
Thanks I will start that now

---

### Post by hoboy on 2011-02-26
> **doas777 said:**
> yup. in the VBox window, go to Devices -> Install guest Additions
it will mount a virtual CD to your Win7 optical drive, so autorun the disk, and it will walk you through the tools install.

after that, once everything is installed and you have rebooted, rclick your desktop and select "Screen Resolution" to adjust the size of the window. the resolution must be less than or equal to the resolution of the host PC. if you want to use fullscreen or seamless mode, I recommend setting the res equal to the hosts screen res.

just a note, every time you upgrade VBox, you will have to reinstall the client tools. not a big deal. if you virtualize a linux OS as guest, you will also have to reinstall them after kernel upgrades.

Thanks it made a difference to install client tools.
How do I get ubuntu 10.10 resolution ?

---

### Post by hoboy on 2011-02-26
> **doas777 said:**
> yup. in the VBox window, go to Devices -> Install guest Additions
it will mount a virtual CD to your Win7 optical drive, so autorun the disk, and it will walk you through the tools install.

after that, once everything is installed and you have rebooted, rclick your desktop and select "Screen Resolution" to adjust the size of the window. the resolution must be less than or equal to the resolution of the host PC. if you want to use fullscreen or seamless mode, I recommend setting the res equal to the hosts screen res.

just a note, every time you upgrade VBox, you will have to reinstall the client tools. not a big deal. if you virtualize a linux OS as guest, you will also have to reinstall them after kernel upgrades.

Thanks don't bother I have googled.

---

### Post by doas777 on 2011-02-26
> **hoboy said:**
> Thanks it made a difference to install client tools.
How do I get ubuntu 10.10 resolution ?

in ubuntu, it depends on what kind of video card driver you have installed. start by going to 
System -> Preferences -> Monitors. what is the resolution there? if the applet does not open, or if the res reads as 800x600, look to see if you have an icon for Nvidia Settings, or for AMD/ATI CCC LE, then those would be where the settings are. 

just to be clear, ubuntu is the host, and win7 is the guest, right?
in that case, be sure not to change the ubuntu resolution; just check to see what it is.


Edit: 
Ahh. Glad to see you got it going. 

gl&hf

---

### Post by hoboy on 2011-02-26
> **doas777 said:**
> in ubuntu, it depends on what kind of video card driver you have installed. start by going to 
System -> Preferences -> Monitors. what is the resolution there? if the applet does not open, or if the res reads as 800x600, look to see if you have an icon for Nvidia Settings, or for AMD/ATI CCC LE, then those would be where the settings are. 

just to be clear, ubuntu is the host, and win7 is the guest, right?
in that case, be sure not to change the ubuntu resolution; just check to see what it is.


Edit: 
Ahh. Glad to see you got it going. 

gl&hf

Thanks for your time everything is working like a charm.

---

### Post by AlexanderDGreat on 2011-03-27
I'll choose VMware Player (FREE) over VirtualBox anytime of the day.

Search for the thread, VMware Player VS VirtualBox, something like that.

---

