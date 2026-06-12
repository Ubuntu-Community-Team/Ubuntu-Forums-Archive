---
title: "Ubuntu Studio 64 bit install problems"
date: 2010-05-29
forum: Ubuntu Studio
---

### Post by acidblue on 2010-05-29
The install goes well, no errors.
But I don't think grub installs correctly.

I have a 3 drive system with WinXP, Ubuntu 10.04/64bit and Ubuntu Studio 64 bit.
The MBR is on the WinXP drive, after the install and a reboot, Ubuntu Studio isn't listed 
in the boot menu, I can boot into my other OS's and 
view the drive Ubuntu Studio is installed on, I can see the usual files
on the Studio drive so it appears it did install.

I chose to have grub installed on the first drive which is the WinXP drive with the MBR.
Should I try and re-install grub?
Can I do this with out having to do a complete re-install?

My drives are set up like this:
WinXP; first ATA drive, cable select as master.
Ubuntu Studio; second ATA drive, cable select as slave.Shares IDE slot with master.

Ubuntu 10.04 First and only SATA drive.

---

### Post by trulan on 2010-05-29
So is your Ubuntu SATA install controlling Grub or is your Ubuntu Studio ATA Slave controlling Grub?  When you install grub to the MBR, it points to whichever drive Grub was installed from, and loads the grub menu from there.  It sounds to me like your Ubuntu installation is controlling Grub, and Ubuntu Studio is not.  My guess is, if you boot into Ubuntu and run ```
sudo update-grub
```, Ubuntu Studio should show up in your grub menu on subsequent reboots.

And yes, you can re-install grub to the MBR without re-installing anything else.  And that should work if you install grub from either Ubuntu or Ubuntu Studio.  Just keep in mind that whenever something like a new kernel is installed in the OS that is not controlling Grub, you'll need to boot into the one that is controlling grub and run sudo update-grub for the new kernel to show in the grub menu.

---

### Post by acidblue on 2010-05-29
Thanks that worked :P

---

