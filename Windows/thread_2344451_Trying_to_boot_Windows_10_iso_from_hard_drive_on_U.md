---
title: "Trying to boot Windows 10 iso from hard drive on Ubuntu"
date: 2016-11-25
forum: Windows
---

### Post by joelsmith on 2016-11-25
Hi! I'm running a tower PC with the Kubuntu variant installed, and I partitioned the hard drive to dual-boot Windows 10 with Kubuntu. I formatted the Windows partition as NTFS, and I copy/pasted the Windows 10 iso (it's the only copy of Windows 10 I have) over to the partition. Now I'm wondering how I can boot the Windows 10 iso directly form the drive partition. Booting the iso from a USB pendrive won't work, as my computer won't mount USB drives in BIOS, it only mounts USB drives with Dolphin open. Of course I don't have DVDs big enough to boot Windows with that option. 

I want to boot the Windows 10 iso from the partition where it resides. Is there a way to do this? Doing extensive research online didn't seem to show any answers.

---

### Post by howefield on 2016-11-25
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2016-11-25
> s there a way to do this?

No, not the way you are describing booting an iso directly by just copying the iso to the ntfs partition.  Grub will directly boot any Linux system but chainloads to boot any windows whether it is installed or an extracted iso file.  The link below describes in detail how to do this from a flash drive but the method also works to boot from an ntfs partition on a hard drive.  Did it myself with windows 10.  You would need to create an ntfs partition which is slightly larger than the iso file and then another ntfs partition on which to do the actual install.  When finished, you can delete/format the partition on which you had the extracted windows iso and add it to the windows partition on which you installed windows.  Best to have these two partitions continguous as that will greatly simplify the process.  

If you get an error trying to use Disk Image Mounter indicating the file size is too large, you will have to loop mount before you copy.

You will also need to know if your Kubuntu is installed using MBR or UEFI/GPT as windows will need to be installed with the same method or you will have problems.  I would suggest you read through the page before beginning.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

