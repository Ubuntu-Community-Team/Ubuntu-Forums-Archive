---
title: "virtualbox won't detect usb drives"
date: 2009-02-14
forum: Virtualisation
---

### Post by Arminius on 2009-02-14
ok, I'm using the non ose version of virtualbox, the one that has usb support
I have an apple iphone and a usb drive set to active.
and yet when I start up the xp, and u look in my computer, the iphone is there, but the usb drive is not, and I really need that drive it's got all my backed up data that ubuntu can't run :(
so any ideas on how to solve this?

I took 2 screenshots to show u all, but they wouldn't add right, is it only possible to add images that are on the net? or can I add images that are sitting on my desktop?

---

### Post by Arminius on 2009-02-14
I had a closer look and every usb device I have installed, when the virtual xp is up it reads every one except the iphone as unavailable, they are all greyed out?
why is that happening and how would I fix it?

---

### Post by bapoumba on 2009-02-14
Moved to Virtualization.

---

### Post by HotShotDJ on 2009-02-14
> **Arminius said:**
> I had a closer look and every usb device I have installed, when the virtual xp is up it reads every one except the iphone as unavailable, they are all greyed out?
why is that happening and how would I fix it?[http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1)

---

### Post by Arminius on 2009-02-15
I'm afraid that post wasn't much help HotShotDJ, all my usb devices are still greyed out

---

### Post by HotShotDJ on 2009-02-15
> **Arminius said:**
> I'm afraid that post wasn't much help HotShotDJ, all my usb devices are still greyed outYou need to provide me some clues as to what you have done to enable USB support. Also, it would help me if you would provide the information requested in the trouble-shooting section entitled "USB Devices are visible under Devices --> USB Devices, but they are greyed out."  With what I know right now, I cannot even begin to guess about what might be the cause of your trouble.

---

### Post by Arminius on 2009-02-16
well if it helps I gave up on virtualbox, and installed vmware workstation, but it's doing the exact same thing, in the vmware section it can detect the usb drive, but in the actual xp side of things, never shows up in the my computer, never detects it

but I'm finding it much easier to transfer files back and forth so I'm moving my norton ghost back up files over to xp, unpacking them there then moving them back, but still it would be 5 times quicker if vmware could detect the western digital my book

---

### Post by captain_conrad on 2009-02-24
hi guys

I have just installed virtualbox and just gotten my XP running. The internet even works wirelessly on the windows XP inside virtualbox, i am very impressed!!!!!

But i cannot pick up any of my 4 usb ports. Its literally a brand spanking new machine (the virtual XP one), so it hasn´t had anything done on it. I do however use a mouse that is a USB mouse, and the mouse works just fine inside the virtual machine. Strange!?!

PLain and simple, how do you activate a virtual machine´s ability to pick up and use the USB ports on the Host Machine?

Thank you for your help guys

Captain Conrad

---

### Post by Arminius on 2009-02-25
exact same thing happened to me conrad, I installed xp on virtualbox and exactly as you described, but I tried using VMware Workstation instead.
same thing happened, then I installed Service pack 2 and it solved all my problems, so try installing SP2 on your virtualbox and let me know if that fixes it, if it does I would like to go back to virtualbox because VMware workstation is mind numbingly slow

---

### Post by HotShotDJ on 2009-02-25
> **captain_conrad said:**
> But i cannot pick up any of my 4 usb ports. Its literally a brand spanking new machine (the virtual XP one), so it hasn´t had anything done on it. I do however use a mouse that is a USB mouse, and the mouse works just fine inside the virtual machine. Strange!?Not strange at all.  VirtualBox does not directly access the USB mouse or your keyboard.  It uses a virtual driver for those devices which allows it to share them with the host OS.  You have not told us what version of VirtualBox you are using.  If you are using virtualbox-OSE (the version provided by the standard Ubuntu repositories) then you will not be able to use most USB devices with it.  Only the PUEL version supports USB.  In fact, the latest version now supports USB with minimal configuration. For proper installation of the PUEL version, see: [http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

---

### Post by Arminius on 2009-03-01
I ment service pack 2 for windows xp
u do the windows updates, and after number 2 u go to control panel, click on system, then go to the hardware tab, then click on device manager, there should be a few yellow exclamation points!! look for the usb related one, tell it to reinstall the drives, this made all my usb's be recognised.

---

### Post by captain_conrad on 2009-03-03
hi guys

right, heres what i have done.

Firstly i went to the virtualbox website [http://www.virtualbox.org/](http://www.virtualbox.org/) and i downloaded the 2.1.4 version. (Obviously got rid of my previous version)

Then I set up my virtual machine.

Then i followed the post that HotShotDj posted a link to. Its the HowTo on getting the USB working. Well I followed it, did the whole thing (except that i got my virtualbox directly from the virtualbox website)
and viola!
All USB works perfectely!

My point is... That HowTo is not obsolete, I found it very usefull, in fact, my version 2.1.4 did not have usb working straight away, it only worked after i had followed the instructions in the HowTo post.

Thank you HotShotDJ!

---

### Post by captain_conrad on 2009-03-03
Ps: arminius, i did get the service pack 2 for windows, and i did go to the harware manager in my system properties, and clicking on ¨update driver¨ did not work... it said that it could not find a better version of the driver already installed. So it had obviously already installed the correct drivers. I think? Well in my previous post i explained what eventually DID work for me. Follow HotShotDJ´s HowTo post. Good luck =o)

---

### Post by Arminius on 2009-03-04
oh well :) it worked for me conrad, must have different hardware and drivers, who ever comes after us with the same problem can try both solutions

---

### Post by gacostac on 2009-03-25
> **captain_conrad said:**
> Ps: arminius, i did get the service pack 2 for windows, and i did go to the harware manager in my system properties, and clicking on ¨update driver¨ did not work... it said that it could not find a better version of the driver already installed. So it had obviously already installed the correct drivers. I think? Well in my previous post i explained what eventually DID work for me. Follow HotShotDJ´s HowTo post. Good luck =o)

HotShotDJ´s instructions worked for me as well!! thanks a lot :)

---

