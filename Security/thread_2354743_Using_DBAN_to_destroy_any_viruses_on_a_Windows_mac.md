---
title: "Using DBAN to destroy any viruses on a Windows machine"
date: 2017-03-05
forum: Security
---

### Post by John_Patrick_Mason on 2017-03-05
Would it be advisable/safe to use the application DBAN to destroy any viruses on an infected Windows machine, before reformatting the hard disk using the Disks application on a live Ubuntu DVD, before popping in an OEM Windows 7 installation disk? I'm asking whether it would be safe because I'm afraid of wiping the BIOS when using DBAN, rendering my computer unbootable.

---

### Post by opsusec on 2017-03-06
i wouldn't stress wiping the BIOS in all honesty, there's always a fix for that. The grub bootloader is a beautiful thing. personally what i would do is flash the factory image on said device, run rkithunter, then proceed to sift through the filesystems myself. encrypt it with LVM  and wipe it three times, what this will do is render slight sections of the drive quarantined and they shouldn't be able to communicate with said new operating system.

or just buy a new drive.

---

### Post by sudodus on 2017-03-06
DBAN overwrites the HDD but does not touch the BIOS.

---

### Post by opsusec on 2017-03-06
> **sudodus said:**
> DBAN overwrites the HDD but does not touch the BIOS.

I've never even found myself having to use this, normally I just wipe them. If worst comes to worst he can inject into the original MBR and flash grub there.

---

### Post by Habitual on 2017-03-06
Just wipe.
If you're concerned, format the target twice.

---

### Post by John_Patrick_Mason on 2017-03-06
[QUOTE=opsusec]i wouldn't stress wiping the BIOS in all honesty, there's always a fix  for that. The grub bootloader is a beautiful thing. personally what i  would do is flash the factory image on said device, run rkithunter, then  proceed to sift through the filesystems myself. encrypt it with LVM   and wipe it three times, what this will do is render slight sections of  the drive quarantined and they shouldn't be able to communicate with  said new operating system.[/QUOTE]

OK, now I'm lost. What do you mean by flashing the factory image? What image? I can edit configuration files in Linux using vi, but that's about it.

[QUOTE=sodudus]DBAN overwrites the HDD but does not touch the BIOS.[/QUOTE]

Once I wipe the hard drive, do I have to use the disks application to reformat the hard drive to NTFS in order for the Windows 7 OEM disk to run, or can I skip that step and have the Windows 7 install disk do the formatting?

---

### Post by deadflowr on 2017-03-06
> Once I wipe the hard drive, do I have to use the disks application to reformat the hard drive to NTFS in order for the Windows 7 OEM disk to run, or can I skip that step and have the Windows 7 install disk do the formatting?
I cannot remember ever installing Windows on a pre-partitioned disk.
I almost always do it to a totally blank disk or empty partitions.
As long as the installer can see the disk, no partitions needed, as far as I can see.

---

### Post by sudodus on 2017-03-06
My knowledge of Windows is rusty, but I am almost sure that the Windows installer can do the formatting.

It can also use a preformatted drive, which is good if you intend to dual boot, and prepare partitions for both Windows and Ubuntu.

---

### Post by John_Patrick_Mason on 2017-03-06
OK, I'm gonna leave this thread open a little longer in case if I run into any issues when I attempt to reinstall Windows.

---

### Post by Habitual on 2017-03-06
If it's empty and the first partition on the disk, Windows should love it.
That's been my experience.

---

### Post by bashiergui on 2017-03-09
> **John_Patrick_Mason said:**
> Would it be advisable/safe to use the application DBAN to destroy any viruses on an infected Windows machine, before reformatting the hard disk using the Disks application on a live Ubuntu DVD, before popping in an OEM Windows 7 installation disk? 
Professionals will wipe the drive by overwriting the entire disk with 0s or random 1s and 0s (which is what DBAN will do). Then they install the new operating system. It is an unnecessary step to reformat the disk with a live dvd because Windows will overwrite it during installation.

---

### Post by HermanAB on 2017-03-10
There are many ways to overwrite a whole disk using a Linux install CD/USB stick:
# cat /dev/zero > /dev/sda
# dd if=/dev/zero of=/dev/sda

You can use /dev/urandom also, but it may confuse the Windows installer.

---

