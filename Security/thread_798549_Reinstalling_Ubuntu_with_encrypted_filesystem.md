---
title: "Reinstalling Ubuntu with encrypted filesystem"
date: 2008-05-18
forum: Security
---

### Post by suruena on 2008-05-18
I've upgraded to kubuntu 8.04 in my laptop (using the alternate CD), this time with disk encryption. I followed very closely the next howto:

[http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

So the windows and /boot partitions aren't encrypted, and then one big encrypted partition which includes the swap, the root filesystem, and the home partitions.

I'm happy with the current configuration, but my doubt is if I can reinstall the system without having to format again the whole encrypted partition. That is, whether the ubuntu CD installer will recognize the existing encrypted partition, and allow me to write the current passphrase, then decrypt the root, swap and home partitions, and finally to just format the root and swap partition and reinstall the system without affecting the data at /home

I made some tests, booting with the CD. When doing the manual partitioning the filesystems of the boot and windows partitions are recognized, but not the encrypted partition. Then, I can specify that the big partition is a Encrypted LVM partition and that I don't want to remove the data. However, when configuring the encrypted partition the installer ask for a _new_ passphrase. Am I doing something wrong?

Thanks!

---

### Post by hyper_ch on 2008-05-18
as far as I know it's not possible yet to reinstall on an encrypted filesystem.

---

### Post by Lycaon on 2008-05-18
I would agree with hyper_ch, i don't think it's possible because it's "rubbish" data for an outsider..

---

### Post by RAOF on 2008-05-18
It should be possible to reinstall on the encrypted partition, but I'm not sure how much of it is automated.  The worst-case scenario is that you have to switch to a virtual terminal (which the alternate installer provides) and manually unlock your encrypted partition using cryptsetup.  That should then allow the partitioner to use the partitions inside your crypt device.

---

### Post by hyper_ch on 2008-05-19
would that then still generate correct boot entries in the grub menu.lst? That's where I see a possible problem if you load the encrypted partitions manually.

P.S.: Upgrading works excellent... I did it with 7.04 to 7.10 (wasn't fully encrypted the but just a few partitions that I manually encrypted back then)

---

### Post by RAOF on 2008-05-19
> **hyper_ch said:**
> would that then still generate correct boot entries in the grub menu.lst? That's where I see a possible problem if you load the encrypted partitions manually.
...

I don't know.  I think it should, but I've never tried it.  If you try it and it doesn't work, please file a bug.  It should work :).

---

### Post by hyper_ch on 2008-05-19
I'll try on the vbox tonight :)

---

### Post by hyper_ch on 2008-05-19
so, I tested it now... installed an ubuntu 8.04 encrypted (manual encryption with a /boot and a / partition) in vbox.

After it run fine, I just started over again, when I got to select how I want to partition the drive (guided, guided lvm, guided lvm encrypted, manual) I pressed alt-f2 to enter dos box.

I then run fdisk -l to see what the partitions are and then I tried to open the encrypted partition but it fails. I have a screenshot here.

I don't know why it failes....

I also tried to luksOpen /dev/sda2 but that did not work either.

EDIT: I had to modprobe aes ;)

---

### Post by hyper_ch on 2008-05-20
Hmmm, reinstall went ok into an already encrypted partition by
(1) depmod aes during installer
(2) crypt luksOpen /dev/sda5 sda5_crypt
(3) going back to the partitioner

HOWEVER after reboot the system never gets a password entry and just stops at the screenshot (vBox)

---

### Post by RAOF on 2008-05-20
Right.  It looks like the crypttab hasn't been set up correctly.  You should be able to boot by running cryptsetup from the busybox prompt to unlock the partitions, then exit-ing the busybox to continue booting normally.  Does that work?

---

### Post by hyper_ch on 2008-05-21
I have to try tonight but it seems not like an issue with crypttab. Crypttab is in /etc and this is fully encrypted... I would first need to enter the password for the root partition and then the system could use crypttab somehow... but I don't even get asked to enter the password for the root partition.

---

### Post by MBdocotr on 2008-05-21
Original New and Used Mercedes Electronics Parts. Mercedes TV tuner, Head Unit, Comand (Command), CD changer, Passenger Mercedes rear screen, Mercedes remote control, Voice recognition, Audio Gateway, DVD player, Prologic, APS, W211, S and E class comand HU with MP3, DVD, RDS, Dolby digital, Dolby 5.1, Dolby surround, Harness, I-Pod, CarPC, Retrofit. For additional information, order or technical support call 212.660.2905 or 213.291.0192 
For the partner programm and cooperation, contact [email]partner@mbdoctor.com[/email], installers from all countrys needed. 

PHONE KIT BLUETOOTH

S H O P                G A L L E R Y

Click for 

Online shopping       Gallery     Installation

Original New and Used Mercedes Electronics Parts. Mercedes TV tuner, Head Unit, Comand (Command), CD changer, Passenger Mercedes rear screen, Mercedes remote control, Voice recognition, Audio Gateway, DVD player, Prologic, APS, W211, S and E class comand HU with MP3, DVD, RDS, Dolby digital, Dolby 5.1, Dolby surround, Harness, I-Pod, CarPC, Retrofit

for additional information, order or technical support call 212.660.2905 or 213.291.0192

 

MBdoctor is not affiliated with Mercedes Benz, Mercedes-Benz AG, Mercedes-Benz USA, or Daimler Chrysler. MBdoctor's website and it's contents, are not endorsed or affiliated with Mercedes-Benz AG, Mercedes-Benz USA, or Daimler Chrysler, Nothing in this website is endorsed or affiliated with Mercedes-Benz AG, Mercedes-Benz USA or any of it's dealerships. 

 MBdoctor  2003 (c)


[http://mbdoctor.com/](http://mbdoctor.com/)

[http://mbdoctor.com/installation.html](http://mbdoctor.com/installation.html)

[http://mbdoctor.com/shop/index.php?manufacturers_id=10](http://mbdoctor.com/shop/index.php?manufacturers_id=10)

[http://www.mbdoctor.com/gallery/main.php](http://www.mbdoctor.com/gallery/main.php)

Affordable Web Hosting

Copyright © 2003 MBdoctor Inc. All rights reserved.
212.660.2905 or 213.291.0192




Thank you for shopping with us!!

---

### Post by RAOF on 2008-05-21
But does crypttab have the correct contents?  If I remember correctly, that's where the cryptsetup mojo in the initramfs is generated from.

So, options include: not-correct contents of crypttab, or need to run update-initramfs to make the initial ramdisk know about the crypt setup.  There are probably other options, but those are the two that spring to ming.

---

### Post by John Wiersba on 2009-07-05
See _[HOWTO: install and reinstall on an encrypted LUKS/LVM system]("http://ubuntuforums.org/showthread.php?p=7576717")_
See _[HOWTO: re-install / upgrade over existing dm-crypt / LUKS system]("http://ubuntuforums.org/showthread.php?t=1034910")_

---

