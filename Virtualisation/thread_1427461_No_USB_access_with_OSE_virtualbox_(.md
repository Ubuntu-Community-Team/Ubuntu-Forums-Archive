---
title: "No USB access with OSE virtualbox :("
date: 2010-03-11
forum: Virtualisation
---

### Post by Beowulf.1000 on 2010-03-11
EDIT::SOLVED! Very simple solution actually-- from the VB (virtualbox) menu I chose to create a new shared folder, then located my plugged in flashdrive, clicked okay. Outside of the VB I also made another shared folder in my home folder in linux called vbox-common so I could share files between both my usb drive, my linux system, and the virtual WindowsXP.  Okay, then with virtual WinXP fired up, I go to My Computer, go to the Tools menu (of My Computer) and choose the option there for mapping a network drive. I chose the letter U: for mapping a drive to my usb flashdrive I set up earlier from VB, and I chose the letter V: for mapping a drive to my vbox-common folder I set up earlier in my linux home folder and then had identified as a shared folder through VB. I also checked the box to make the mapped drive permanent when mapping each drive, or at least I recall doing that for the flashdrive (USB). I tested it-- yanked my usb flashdrive, shutdown WinXP, turned WinXP back on with my usb drive plugged in, and there were my files on my usb drive! So, I guess the PUEL version of virtualbox is not really needed if all it offers is usb support-- because it took me less than 10 minutes to set up usb support doing what is described here, which really is not hard at all. 

*I can't figure out a way to access my USB drive through an installed OSE virtualbox Windows XP guest. Ubuntu 9.10 hosting virtualbox OSE host. I think I just read somewhere that if I want USB access I will need the PUEL edition of OSE? That sort of stinks if true, just after I have WinXP installed just fine and dandy in the OSE version of virtualbox. Do I really need to go with PUEL virtualbox to get USB access, or is there some workaroun*d?

---

### Post by squaregoldfish on 2010-03-11
Just for information, you do need the PUEL version of VirtualBox to get USB access working. However, it's no big deal, since the PUEL version will happily run any VMs you set up with the OSE version - there's no need to recreate them.

Steve.

---

### Post by Beowulf.1000 on 2010-03-11
Perhaps you could define "USB access"? Because I do not have PUEL, I have OSE, and I have what I call usb access --- access to my usb flashdrive, usb external drive, usb cable to my portable mp3 player. So there is at least that sort of USB access with OSE, no PUEL needed. 

Now if you mean USB access in general -- including other devices like MIDI keyboards, and plug and play USB without requiring network mapping like I did, then that might be true-- I do not know since I do not have nor have tried the PUEL virtualbox. Perhaps you or someone could be so kind as to clarify this so I understand the added USB access PUEL would provide over what I have with OSE?

> **squaregoldfish said:**
> Just for information, you do need the PUEL version of VirtualBox to get USB access working. However, it's no big deal, since the PUEL version will happily run any VMs you set up with the OSE version - there's no need to recreate them.

Steve.

---

### Post by d3v1150m471c on 2010-03-11
plug in your usb. On the machine tab navigate to shared folders and create one for the usb. For xp, run the command "explorer". Go to entire network>virtualboxsharedfolders>yourusb.

---

