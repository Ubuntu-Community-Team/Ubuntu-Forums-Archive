---
title: "Pop!_OS Not Booting...&quot;No known boot loader is installed in the MBR of /dev/sda&quot;"
date: 2020-04-03
forum: Ubuntu/Debian BASED
---

### Post by m52go on 2020-04-03
Would someone mind taking a quick look at this paste:
[http://paste.ubuntu.com/p/hmFMJhMZnJ/](http://paste.ubuntu.com/p/hmFMJhMZnJ/)

Machine is an XPS 9560. I only care about the Pop!_OS installation on the main 1TB drive (`/dev/nvme0n1p3` it seems?).

I think I might have screwed things up when I installed Android-x86 last week...their [documentation]("https://www.android-x86.org/releases/releasenote-8-1-r4.html") notes that the software makes some changes to GRUB, but not exactly what they are. But I did restart once after that install and the machine booted back into Pop just fine, so I'm not sure. The Android thing was just an experiment...I just really want to regain access to my Pop install.

I would hugely appreciate your help!

There are other threads that seem similar, but I really don't want to take a chance with this...

---

### Post by oldfred on 2020-04-03
Boot-Repair uses the older bootinfoscript for first part of report that details drive & files inside drive. But bootinfoscript has not been updated for NVMe drives and I do not think it includes the systemd boot configuration files.

I do not know systemd boot, but have these references.

POP!OS uses systemd boot:
Gummiboot is dead, of course, because it was spun into systemd 2015

Systemd boot loader spec (was gummi boot:
[https://systemd.io/BOOT_LOADER_SPECIFICATION](https://systemd.io/BOOT_LOADER_SPECIFICATION)
[https://www.freedesktop.org/wiki/Software/systemd/systemd-boot/](https://www.freedesktop.org/wiki/Software/systemd/systemd-boot/)
 systemd-boot (f. gummiboot)
[https://blobfolio.com/2018/06/replace-grub2-with-systemd-boot-on-ubuntu-18-04/](https://blobfolio.com/2018/06/replace-grub2-with-systemd-boot-on-ubuntu-18-04/)

You boot is here:
```
Boot0004* Pop!_OS 18.04 LTS    HD(1,GPT,dd4e1e02-70b3-41b3-9301-9be6ba9d2752,0x1000,0xf8fff)/File(EFIsystemdsystemd-bootx64.efi)
```

And then in /EFI/systemd/ should be a conf file with the details as explained in links above.

---

### Post by yancek on 2020-04-03
You appear to have 2 EFI partitions on the SSD, see lines 57 & 58 of boot repair.  You might try mount them to take a look at what is there and see if you can find the PopOS files:  

> /dev/nvme0n1p1   4C8E-2F08                              vfat
/dev/nvme0n1p2   4C8E-378E                              vfat   

If you look at lines 27 and 276, you will see that you have 2 entries for PopOS.  Go into the BIOS firmware on boot and try to select either of them to see if you can boot.  If one works and the other fails, you've got your answer so you can delete the other.  If you encrypted PopOS then it would appear to be on the 3rd partition of the SSD.  I'm not familiar with LVM or systemd so am not sure what effect that would have.  Hopefully the links oldfred gave you will help. 

I would suggest that if using Android is just a test or an experiment, that when you get PopOS working and want to try Android again, you install VirtualBox and install Android there.  Android uses a modified Linux kernel and the ext4 filesystem but that's about where the similarity ends.  One of the modifications it makes is that there is no grub.cfg file but there is an android.cfg file which is similar to grub.cfg.  Basin Linux commands such as grub-mkconfig, fdisk, gdisk and parted are also not available.  Well, good luck!

---

### Post by m52go on 2020-04-16
oldfred, yancek -- thank you a TON. I wasn't able to restore access to the installation, but your clues did lead me to another resource which showed me how to access my drive in live mode to get some very very important files. Would've been kind of screwed without those files...

So then I just nuked the whole thing and reinstalled.

Thanks again!!!!!!!!!!

---

