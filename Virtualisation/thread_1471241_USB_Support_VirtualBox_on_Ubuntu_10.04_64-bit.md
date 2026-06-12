---
title: "USB Support VirtualBox on Ubuntu 10.04 64-bit"
date: 2010-05-03
forum: Virtualisation
---

### Post by manco on 2010-05-03
Okay, so I installed the AMD64 version for Karmic listed [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

I can't get USB support working.  I've added myself to the group "vboxusers", but every time I open up (in my case, Windows XP), under the USB icon it says "<no devices available>".  This is with the Guest Additions installed, I might add.

I can get by without it, but back in 9.10 (32-bit) USB support worked out of the box, no problems.

Can anyone help?

Thanks!

---

### Post by Ginsu543 on 2010-05-04
I'm trying to better understand your problem. When you say USB icon, do you mean the small blue usb icon in the status bar at the bottom of the screen? If so, then it might be that you haven't manually added the usb device you want VirtualBox to access. To do this, go to the menu at the top of the screen and click on "Devices" (it's next to "Machines"). You should then be able to see a menu item called "USB Devices." If you hover your mouse over it, you should see a list of usb devices available to you. Click on the one you want, and it will be added to VirtualBox. Once you do that, it should also appear under the USB icon at the bottom of the screen.

---

### Post by Euphorion on 2010-05-05
Hello

I have exactly the same problem. When setting up a machine or entering the USB section in the machine parameters, a window pops up informing me that Virtual Box has no USB support owing to the fact that the USB File System USBfs (?) and another driver is missing.

According to the popup the Ubuntu system is missing the USB file system. The strange thing is however in Ubuntu USB works very well, I can insert memory sticks and drives they are all detected and mounted.

Do I need to install the USB file system and associated drivers ? Or will Sun release a new version of Virtual Box for Lucid.

In Karmic 32bit I installed VirtualBox and it worked a treat including USB straight out of the box.

The USB Icon at the bottom left of the screen is present. Should I try to add USB Device with the Machine Menu I see no entries.

Hope you can help us - thanks in advance.

---

### Post by Ginsu543 on 2010-05-05
Euphorion, did you install VirtualBox from the Lucid repos or did you download the .deb file from VirtualBox.org? If you got it from the repos, then it's the OSE version which does not support USB. You need to get the PUEL version available from the main website.

If you already have the PUEL version, you may be having trouble seeing USB devices because you have not added yourself to the vboxusers group. If so, then go to System --> Administration --> Users and Groups. Click on the "Manage Groups" button and look for "vboxusers" group. If it's not there, go ahead and add it. Once you get into the "vboxusers" properties, make sure that there is a check by your user name. Click "OK" and close. Hopefully, now you will be able to see your USB devices under "Machines" in the menu.

---

### Post by matza55 on 2010-05-05
Had this problem too. But in my case it's the writer (Samsung ML1750, which is missing. Everything else works?!

---

### Post by Peter09 on 2010-05-05
I had this line in /etc/fstab
 
> none /proc/bus/usb usbfs devgid=125,devmode=664 0 0 
 
which was commented - provide vbox usb support - 
 
This gave me a working usb interface to vBox.
 
Note though that on upgrade to Lucid this line stopped the system booting.

---

### Post by Perryg on 2010-05-06
This seems to be an issue with VirtualBox and the deprecation of hal and usbfs in 10.04. Upgrades to 10.04 from 9.10 did not seem to be affected due to hal still being in the OS after upgrade AFAIK.  Virtualbox versions prior to 3.2.0 will see these problems.  VirtualBox ver.3.2.0-Beta-1 has the support if you want to download the PUEL version from VirtualBox and it does work.

Note: Beta 2 is due out soon if you want to wait a bit.

---

### Post by Euphorion on 2010-05-07
I have tried the above mentioned solutions. An upgrade to the Beta 1 version has put an end to the pop up that no USB file system and Dev is present. I have checked my membership of the group Vbox users and I was a member. I have also recompiled the drivers as shown.

The current situation that I now have, is that Memory Sticks can be entered into the USB Filter, when the virtual machine is started the memory stick is removed from the Ubuntu desktop and in any open Nautilus. The USB Icon bottom right says that the stick is detected and in action, but the host operating system in virtual box does not see the stick.

The only way I can use the stick is to include it as an external directory and issue a net use command in the host operating system (Windows). For the time being I can live with this work around.

Will upgrade to Beta 2 when available and see if that makes things better.

---

### Post by Euphorion on 2010-05-19
Have now installed VirtualBox Beta 3 and have managed to get USB working. I upgraded the Beta 1 version to Beta 3, reinstalled the additions and restarted my computer.

I then connected the USB devices (in my case Memory Sticks) and checked that they are correctly listed in the VirtualBox Settings USB. I then started Windows in Virtual box. Went into Windows Settings, Device Manager and found that a USB driver had a yellow question mark. I then used the context menu to reinstall the windows USB driver, the install was carried out successfully and thereafter I now see my Memory Sticks in Explorer and can access them via the installed windows programs.

Hence my USB in VirtualBox is back to normal.

---

