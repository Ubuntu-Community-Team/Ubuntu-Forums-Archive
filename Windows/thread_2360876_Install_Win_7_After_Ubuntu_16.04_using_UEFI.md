---
title: "Install Win 7 After Ubuntu 16.04 using UEFI"
date: 2017-05-09
forum: Windows
---

### Post by jachin99 on 2017-05-09
I had a machine crap out on me to the point where I couldn't get a BIOS menu, or any OS to load.  The only available solution I found was boot a linux live CD, and install Ubuntu on corrupted HDD.  This gave me a working BIOS, HDD, and OS so I have the option of stopping here if that were all I needed.  Its not, and in order to get my home network to where I would like it I need a working copy of Windows 7 on the machine for Windows Media Center Extender use (Something I don't believe I can easily accomplish via VMs inside linux).  I don't particularly mind if I end up with a dual boot configuration with Win7/Linux or if its just Win 7 but either way, I need to find a way to put Win 7 on this machine so here are my questions.


How do I create a new hard drive partition for the windows install in Ubuntu if neccessary?  I have read a few articles, and understand the basics, such as what dev, sda, sda1, etc. mean but thats about it. 

Can I install Win 7 on a Ubuntu machine with no windows partitions while keeping the GPT scheme?, and if so, How? 

-I installed Ubuntu using UEFI because I did not want to change any default settings, and end up with a failed install. 

If I can't use UEFI, how would I go about switching to a legacy boot configuration without breaking Ubuntu?

Thanks for whatever help you can provide.

---

### Post by yancek on 2017-05-09
> How do I create a new hard drive partition for the windows install in Ubuntu if neccessary?

Use the GParted partition manager which is on the Ubuntu installation media.  If you have Ubuntu on one partition, you need to shrink it and create either unallocated space for windows or an ntfs formatted partition for windows.

> Can I install Win 7 on a Ubuntu machine with no windows partitions while keeping the GPT scheme?,

No.

> I installed Ubuntu using UEFI because I did not want to change any default settings, and end up with a failed install. 


The default install for windows 7 is MBR so you will have to figure how to boot and install it UEFI if you have GPT.  Windows requires UEFI with GPT partitioning.  The microsoft site or some windows forum would be a better place to get information on this.

---

### Post by jachin99 on 2017-05-09
How do I convert to MBR under Ubuntu in order to make it that much easier to create my partition for Win 7?

---

### Post by oldfred on 2017-05-09
You can install Windows 7 in UEFI boot mode on gpt partitioned drive. Windows only boots in UEFI mode from gpt and only in BIOS from MBR.
But you cannot use default DVD as that is BIOS/MBR only, and have to copy to flash drive and move a couple of files around to make it UEFI bootable.

[https://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

> Not all Windows versions are supported. Windows 7 on 64 bits, Windows 8 and newer versions should work.

  After the copy process is finished, look in the USB root folder for the efi/boot directory. If there's a bootx64.efi or bootia32.efi file there, then you're done. You can boot from your USB in UEFI mode.
  If the OS you are making a bootable USB for is **Windows 7**, browse the efi/microsoft folder and copy the entire boot folder from this path one level up in the efi folder. Merge folders if boot already exists.

Here is what to do **if you don't have the bootx64.efi file** in efi/boot folder. Browse the mounted Windows ISO image into the sources folder. Open install.wim (or install.esd) with your archive manager (you will need 7z installed). Go to the path ./1/Windows/Boot/EFI and extract the file bootmgfw.efi anywhere you want. Rename it to bootx64.efi and put it on the USB drive, in the efi/boot folder. If you can't find bootmgfw.efi in install.wim then you probably have a 32 bit Windows ISO or other types of images (recovery disks, upgrade versions).
  You can now boot from your USB in UEFI mode.



---

