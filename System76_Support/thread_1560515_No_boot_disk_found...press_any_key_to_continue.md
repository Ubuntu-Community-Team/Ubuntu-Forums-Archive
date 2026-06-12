---
title: "No boot disk found...press any key to continue"
date: 2010-08-24
forum: System76 Support
---

### Post by pnjabi on 2010-08-24
It seems like I am just having a bad luck with my Meerkat Nettop...something is always going wrong. I bought the system primarily for my parents and they are using it only for browsing. I always make sure that it is updated regularly.

The latest is that I get the error "No boot disk found...press any key to continue". The same message is repeated when I press a key. The only option I have is to reboot which allows it to boot sometimes but then the entire system freezes after 2-3 minutes of browsing (Chrome) and I have to reboot again.

I am typing this after booting using a live CD. While I was in the boot menu I noticed that it did not find any hard drive. I tried running fsck but it is unable to fix it.

fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Couple months ago I was having similar boot issues and I clean installed the system which fixed it. Before that my filesystem got corrupted. As I am typing this I am hearing a beep sound from the system...seems like "spinning" is not smooth or something.

Any help would be appreciated. It seems like hard drive is going bad. Thank You.

-Jaz

Meerkat NeTTop
Ubuntu 10.04

---

### Post by silbak04 on 2010-08-24
If you think your hard drive is going bad, the best bet to do right now is to go ahead and chroot, and back up everything you need by mounting the drives....here's a tutorial that shall help you with chrooting:

[http://superuser.com/questions/111152](http://superuser.com/questions/111152)

---

### Post by jml on 2010-08-25
Here is a link to the System Rescue CD home page.  It's a live CD designed for "system rescue"  This is a free download so it may also be helpful in troubleshooting your computer.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Good luck.

Joe

---

### Post by pnjabi on 2010-08-25
I have my data backed up...so I am not worried about that. What can I do to figure out if indeed my hard drive is going bad? Should I boot with a Live CD and run some hardware tests?
 
> **jml said:**
> Here is a link to the System Rescue CD home page. It's a live CD designed for "system rescue" This is a free download so it may also be helpful in troubleshooting your computer.
 
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
 
Good luck.
 
Joe

---

### Post by dtoronto on 2010-08-25
I seem to remember this issue the first time I installed 64-bit 10.04.  After the install it did exactly what you explained, I think I had to adjust my bios settings to look boot to my ubuntu HDD.

---

### Post by pnjabi on 2010-08-26
I have a 32-bit version installed. Can someone from System76 shed some light on this issue? Thanks.
 
 
> **dtoronto said:**
> I seem to remember this issue the first time I installed 64-bit 10.04. After the install it did exactly what you explained, I think I had to adjust my bios settings to look boot to my ubuntu HDD.

---

### Post by jml on 2010-08-26
Until System 76 responds, here are my thoughts.  The error message means that the boot loader cannot recognize the hard drive.  This can be due to several causes:  1- the master boot record is corrupted, 2- the hard drive is physically damaged, 3- the hard drive got unplugged from the motherboard.

The fact that a live CD does not recognize the hard drive makes me think it's one of the latter two choices.  Given the sound that you are describing it sounds like the hard drive may have experienced a catastrophic failure.  How old is your computer? If it is still under warrantee, contact System 76 by e-mail and arrange to either ship your computer back for repairs, or to have them send you a new hard drive.

---

### Post by pnjabi on 2010-08-26
I'll open the box tonight to see if I can see something in there. The system is less than a year old...I think it is still under warranty. Thank You.
 
> **jml said:**
> Until System 76 responds, here are my thoughts. The error message means that the boot loader cannot recognize the hard drive. This can be due to several causes: 1- the master boot record is corrupted, 2- the hard drive is physically damaged, 3- the hard drive got unplugged from the motherboard.
 
The fact that a live CD does not recognize the hard drive makes me think it's one of the latter two choices. Given the sound that you are describing it sounds like the hard drive may have experienced a catastrophic failure. How old is your computer? If it is still under warrantee, contact System 76 by e-mail and arrange to either ship your computer back for repairs, or to have them send you a new hard drive.

---

### Post by zaphod777 on 2010-08-27
Sounds like you need to re-install grub.

From the liveCD you should be able to re-install
the documentation is pulled from here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


> Reinstalling GRUB 2
There may be times when a user needs to either move or reinstall a GRUB 2 installation. GRUB 2 needs to be reinstalled when a user is presented with a blank screen with only the word "GRUB", no prompt, and no ability to enter commands. This often happens when the MBR of the booting device is altered and GRUB 2 is removed, such as when Windows is installed after Ubuntu. Additionally, if a user cannot boot into an operating system at all, even using the rescue mode mode, a complete reinstallation of GRUB 2 may be necessary.

Reinstalling from LiveCD
If you cannot boot from GRUB 2 review the section Boot Problems and Rescue Mode. If a reinstall becomes necessary follow these instructions. Two methods are presented; both require booting from a LiveCD (Ubuntu 9.10, Karmic Koala or later version). If the first method does not work, follow the second method, which is more complex and contains more options and instructions.

SIMPLEST - Copy GRUB 2 Files from the LiveCD
This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods.

Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".
sudo fdisk -l
If the user isn't sure of the partition, look for one of the appropriate size or formatting.
Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.
Mount the partition containing the Ubuntu installation.
sudo mount /dev/sdXY /mnt
Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot
Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.
sudo grub-install --root-directory=/mnt/ /dev/sdX
Example: sudo grub-install --root-directory=/mnt/ /dev/sda
Reboot
Refresh the GRUB 2 menu with sudo update-grub
If the user wishes to explore why the system failed, refer to Post-Restoration Commands section below.

---

### Post by pnjabi on 2010-08-29
I reinstalled Ubuntu again and see this hard disk error (see attached). The hard disk self-test failed.

Does this mean I need a new hard drive?


> **zaphod777 said:**
> Sounds like you need to re-install grub.

From the liveCD you should be able to re-install
the documentation is pulled from here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by zaphod777 on 2010-08-30
It would look as though it is on its way out I would recommend replacing the HDD ASAP.

---

