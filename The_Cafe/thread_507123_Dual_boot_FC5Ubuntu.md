---
title: "Dual boot FC5/Ubuntu"
date: 2007-07-22
forum: The Cafe
---

### Post by sulblk27 on 2007-07-22
Hello all, I have searched this forum, and others since yesterday...all things that I have tried have been in vain.  Keeping in mind, I just installed this distro last night so if a reinstall is necessary I will not mind.  There are other issues...like the no shutdown, but this one is more important to me.  Boots to ubuntu just fine...trying fc5 is a hold nother ball of wax.  I have posted the fdisk and menu.lst, any assistance will be greatly appreciated.

Disk /dev/hda: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        1655    13189365   8e  Linux LVM

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         248     1992028+   b  W95 FAT32
/dev/hdb2   *         249         757     4088542+  83  Linux
/dev/hdb3             758         784      216877+   5  Extended
/dev/hdb5             758         784      216846   82  Linux swap / Solaris

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-12-Lion
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
boot

title		Ubuntu, kernel 2.6.17-12-Lion (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.17-12-generic
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

title           Fedora Core 5
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-1.2320.fc5 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd-2.6.20-1.2319.fc5.img
quiet
boot

I have tried moving FC5 to the top, using chainloader +1, and a variety of other options I have found.  The most I can get with the current system is file no found.  Another way, starts the boot for fc5 then kernel panic (sort the state I'm in now!):confused:....one of the other erros mount: could not find filesystem '/dev/root' and unable to access resume device (/dev/VolGroup01/LogVol01) when I have LogVol00:confused:.  Anyway...thank you for reading thru this post in order to try and assist a noobie in times of need.

I apologize..I just noted I posted to the wrong thread area

---

### Post by DBStevens on 2007-07-25
"Another way, starts the boot for fc5 then kernel panic (sort the state I'm in now!"

Could you put things back to the point you got this message with one slight change remove the quiet splash from the fc5 kernal line and post the error messages and such ....

---

### Post by igknighted on 2007-07-25
Any particular reason for FC5?  I just had to do an FC5 install in order to get Scalix installed and compared to Fedora 7 (no longer core) its awful.  I am the first person to get annoyed when people rip YUM, but even as recently as FC5 it was nearly unusable.  Now in Fedora 7 it is my favorite package manager.

As for setting up the dual boot, I would reinstall and install the Fedora bootloader to the partition and leave Ubuntu on the MBR.  Then point the fedora entry in Ubuntu's bootloader to Fedora's bootloader (it'll save you work later on... Fedora updates the kernel regularly which would require you to change the bootloader manually if you did it a different way).  The way you do this is with a chainloader entry.  Basically see the instructions on how to dual boot windows and just point the chainloader towards that partition.

EDIT: Oh, if Fedora is on its own disk you can install its grub onto the MBR of its drive (Assuming Fedora is the LVM, which is its norm).  Then you would point the chainloader to the drive, (hd1) most likely.

---

