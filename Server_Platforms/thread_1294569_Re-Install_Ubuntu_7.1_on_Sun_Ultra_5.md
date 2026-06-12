---
title: "Re-Install Ubuntu 7.1 on Sun Ultra 5"
date: 2009-10-18
forum: Server Platforms
---

### Post by DAB1 on 2009-10-18
Hi,  I've got a slight problem which I can't rectify and I was wondering if anyone could help.  I have a Sun Ultra 5 with Ubuntu 7.1 pre-installed. I was given the machine because it had not been used for years. Unfortunately, no one can remember the password to get into it so I need to reinstall an operating system (preferably Ubuntu 7.1).  I thought I could get into OpenBoot, but to no avail and I've read on another forum that Ubuntu 7.1 disables OpenBoot so I'm stuck trying to interrupt the boot sequence to get to a position where I can boot from cdrom. This is a dual hard drive machine, in which it seems the Ubuntu distro is on the second disk (not primary). I've tried removing the ribbon cable from the Ubuntu disk, and booting the other one as primary, but the machine locks up.  Does anyone know how I can interrupt the boot sequence into Ubuntu 7.1, prior to getting to the login prompt, so I can re-install from cdrom  [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)  Thanks

---

### Post by cariboo on 2009-10-18
Why do you need to reinstall because you don't know the password? Can't you start in recovery mode, and just set a new password?

---

### Post by DAB1 on 2009-10-24
Cariboo,  Many thanks for your reply. There isn't a Grub boot loader installed for the Sun Ultra Sparc installation...on power up it goes straight into the boot cycle to the login prompt. So I can't get into recovery mode as you've suggested, unfortunately.  I've been thinking further and it might be the case that the PROM battery is dead and that is probably the cause of my problem. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by viper250 on 2009-10-24
What type of drives? If I remember correctly most sun systems used an scsi drive configuration. you could access the configuration program at boot and change the boot drive but changing the configuration would require re-initialising and formatting the drives.

ide drives on the other hand will work fine if the jumper is set correctly to co-respond to its cable location  your master drive has the grub loaded in the mbr so you should be able to use the recovery console to either edit grub or change the root password 

although re installing will work you will lose any data that is on the drive due to repartitioning and formatting process that is part of install

---

