---
title: "Does Ubuntu 12.10 support RAID"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Penguin360 on 2012-10-04
A newbie question, so please bear with me.

I tried to install Ubuntu 12.10 on my PC with RAID, the installation worked fine, but the PC didn't reboot afterwards. I had to reinstall it with RAID disabled, now it is working. Can Ubuntu be installed with RAID enabled? Or am I missing something?

---

### Post by grahammechanical on 2012-10-04
This is what we want to know.

Alternate CDs which set up RAID during an install are not being provided for 12.10 or any following releases.

The installer is supposed to let you set up RAID but the work is not finished.  I understand that the installer (called Ubiquity) cannot yet handle Desktop RAID.

There have been installation issues with 12.10 over the last few weeks even without RAID thrown into the mix. Let us make sure that your problem is due to RAID or down to another issue.

You say, it did not reboot afterwards. Please explain what happened.

Regards.

---

### Post by Penguin360 on 2012-10-04
Didn't reboot = The Ubuntu logon screen never came up, even after shut down and restart.

I disabled RAID, then reinstalled Ubuntu, everything is fine now. 

I would love to test RAID installation if this will be helpful to everyone, and I can try to reenable my RAID and restall if needed.

---

### Post by dino99 on 2012-10-04
same issue: [http://ubuntuforums.org/showthread.php?t=2066032](http://ubuntuforums.org/showthread.php?t=2066032)

---

### Post by ventrical on 2012-10-05
> **dino99 said:**
> same issue: [http://ubuntuforums.org/showthread.php?t=2066032](http://ubuntuforums.org/showthread.php?t=2066032)


Thanks dino ! :)

 @codingbeaver

I added a post  at:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

so if you want to try this project (or help with it)  .. perhaps you could post there?

thanks.

---

### Post by grahammechanical on 2012-10-05
From the link provided by ventrical I understand that the traditional way to install Ubuntu with RAID is the use to Alternate CD and not the standard live CD/DVD.

> **Requirements**

If you're building a desktop then you need the "Alternate" install CD for Ubuntu. 

As we do not have an Alternate CD for 12.10 then the way to install and set up RAID for the time being is to use the 12.04 Alternate CD and then upgrade to 12.10.

I have been assured by someone in the Quality Assurance Team that once the RAID is set up the upgrade to 12.10 should not break it.

By 13.04 it is hoped that also this can be done using a live CD/DVD.

As has already been mentioned, at this stage of development the installation of Ubuntu and RAID using the live CD is still being tested. Congratulations. You are now a Ubuntu+1 Tester. :)

Regards.

---

### Post by ventrical on 2012-10-05
@graham,

Thanks for that info. 

regards,
ventrical

---

### Post by masgeeks on 2012-10-17
This may sound a bit basic, but... how about using the server version and then afterwards just install the desktop of your liking...???  Unless they took the text based installer away from the server version of 12.10, too, lol.  I've done this in the past, used the server cd to install and setup my raid, and then just install a desktop when I needed on.  Haven't done that in a couple of years, though, but guess I'll have to do it again... since I raid 1 everything here, not just servers.  Its sad they have discontinued the alternate cd... that's what I used for every workstation here, maybe its time to go back to debian...???  :-o

---

### Post by cariboo on 2012-10-17
> **masgeeks said:**
> This may sound a bit basic, but... how about using the server version and then afterwards just install the desktop of your liking...???  Unless they took the text based installer away from the server version of 12.10, too, lol.  I've done this in the past, used the server cd to install and setup my raid, and then just install a desktop when I needed on.  Haven't done that in a couple of years, though, but guess I'll have to do it again... since I raid 1 everything here, not just servers.  Its sad they have discontinued the alternate cd... that's what I used for every workstation here, maybe its time to go back to debian...???  :-o

Instead of installing Quantal, you could wait until Raring Ringtail to see if the raid problem has been fixed when using the Live CD. The other alternative is to use the Mini/Netinst iso.

---

### Post by codedmin on 2012-10-18
The upgrade from 12.04 to 12.10 did't in fach break the raid!

I can't reboot my pc or i will loose it... i can't install the grub because grubs says can't find the raid device....
dmps@dmps-desktop:~$ sudo update-grub2
Gerando grub.cfg ...
Encontrado imagem linux: /boot/vmlinuz-3.5.0-17-generic
Encontrado imagem initrd: /boot/initrd.img-3.5.0-17-generic
/usr/sbin/grub-probe: erro: não foi possível encontrar uma unidade GRUB para /dev/mapper/isw_dfagjfhfdb_Volume0p1. Verifique o seu device.map.
/usr/sbin/grub-probe: erro: não foi possível encontrar uma unidade GRUB para /dev/mapper/isw_dfagjfhfdb_Volume0p1. Verifique o seu device.map.
/usr/sbin/grub-probe: erro: não foi possível encontrar uma unidade GRUB para /dev/mapper/isw_dfagjfhfdb_Volume0p1. Verifique o seu device.map.

dmps@dmps-desktop:~$ ls /dev/mapper/
control  isw_dfagjfhfdb_Volume0p1  isw_dfagjfhfdb_Volume0p2  isw_dfagjfhfdb_Volume0p5  isw_dfagjfhfdb_Volume0p6
dmps@dmps-desktop:~$ sudo df -h
Sist.fichs                            Tama  Ocup Livre Uso% Montado em
/dev/mapper/isw_dfagjfhfdb_Volume0p1   14G   11G  3,0G  78% /

---

