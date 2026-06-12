---
title: "Install WinXP inside VirtualBox - raid driver problem"
date: 2010-05-19
forum: Virtualisation
---

### Post by wolf_3d on 2010-05-19
I'm trying to install Windows XP inside the latest version of VirtualBox but I am unable to install the nvidia raid driver during the Windows XP setup process.

During the Windows XP setup process I have to hit F6 to install the SATA/RAID driver as I have a SATA hard disk. After hitting F6 setup doesn't detect any controllers. I have a floppy disk with the nvraid driver on but it doesn't recognise it during setup. If I don't hit F6 the setup says that it is unable to find any hard disks to install to.

In the virtual machine settings I have specified one storage controller for my DVD drive, a SATA Controller for the hard drive and a floppy controller for the floppy drive.

I have installed the dmraid package as it supports the Nvidia Nforce Raid format but I don't know what I'm doing with it.

---

### Post by pirateghost on 2010-05-19
you dont need to install nvidia raid drivers.  the vm does not see your ACTUAL hardware, its VIRTUALIZED

---

### Post by wolf_3d on 2010-05-19
OK, so what do I do now? I can't get past this stage as it doesn't seem to see my hard drive.

---

### Post by pirateghost on 2010-05-19
> **wolf_3d said:**
> OK, so what do I do now? I can't get past this stage as it doesn't seem to see my hard drive.
change the harddrive controller settings in your virtual machine settings to be ide instead.  you dont have to use sata controller

---

### Post by wolf_3d on 2010-05-19
I'm now getting errors during the setting up windows stage and its giving me errors such as "Cannot install driver CDROM" and "Cannot install driver hard disk" :(

---

### Post by pirateghost on 2010-05-19
that sounds like you have a 'virtual controller' issue
on the vm settings, make sure under storage, you have selected IDE CONTROLLER with type PIIX4

this applies to both the virtual cdrom and the harddisk

---

### Post by wolf_3d on 2010-05-20
Hi, the ide controller is definately PIIX4 (see screenshot attached) but I can't add a seperate one for the cdrom as the option to add add another ide controller is greyed out.

---

### Post by wolf_3d on 2010-05-21
Bump #1

---

### Post by wolf_3d on 2010-05-25
Nevermind, I've worked out what I was doing wrong and I've now got XP working in virtualbox.

---

### Post by rbrown3rd on 2010-05-29
What did you do to get the install to complete?

---

### Post by koala15 on 2010-06-13
How do we learn, if folks will not share?

---

### Post by wolf_3d on 2010-07-01
> **koala15 said:**
> How do we learn, if folks will not share?

> **rbrown3rd said:**
> What did you do to get the install to complete?

Okay,

I kept the settings as it shows in the earlier screenshot.

During the XP installation I chose the FAT32 option instead of NTFS because I only created a dynamically expanding hard drive that was 20GB in size.

I think FAT32 should be used for the smaller hard drives and NTFS is normally used for the larger hard drives.

---

