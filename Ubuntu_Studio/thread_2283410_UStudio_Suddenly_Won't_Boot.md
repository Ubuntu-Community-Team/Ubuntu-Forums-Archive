---
title: "UStudio Suddenly Won't Boot"
date: 2015-06-21
forum: Ubuntu Studio
---

### Post by wmichaelb2 on 2015-06-21
Hi: My US 14.04 LTS 64-bit system, which has run flawlessly until now, suddenly won't boot. 
The first (and only) intelligible error message reads:

```
[   0.523893] Kernel Panic - not syncing : VFS : unable to mount root fs on unknown block (0,0)
```

Then i get a number of lines of what looks like memory addresses or contents, and it hangs. 

I booted SuperGrubdisk, but that was unable to run the repair program. I ran the long test on the SeaTools disk, 
but it found no errors. I booted Puppy Linux off a CD and ran:

```
fsck /dev/sda1
``` 

but it found a clean system with no problems other than a time error, which it fixed. But I still get the above 
message when I boot from the HD. There is no choice for a single user or rescue mode, and it hangs before 
getting to the point where i could look at a system log. 

Has anyone else seen this behavior? Do I need to replace the HD despite it testing fine, or just reinstall?
Or ?

Thanks in advance.

---

### Post by Bashing-om on 2015-06-21
wmichaelb2; Hello;

Given these conditions, and unable to reach the grub menu; I would (RE-)install grub from a liveDVD of the currently installed operating system.
Boot up the liveDVD and determine which partition holds the /boot directory:
```

sudo fdisk -lu
sudo blkid

```
install grub with the proper locations known from the above :
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Here shown is the operating system is installed to device sda hard drive and the '*' /boot directory is "sda1" . Adjust the commands as required.

Reboot into the install, what now is the exact results ? Provide the exact errors if boot is not obtained.

[INDENT][INDENT]seems reasonable to me
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-06-21
Have you tried the RAM? If the drive is testing fine, then that would be the next place to look. The lines of memory addresses could very well be that. 

Take a stick of RAM out, presuming you have two sticks (if you don't, try and grab another one you know works from somewhere). Boot the machine with the one stick in. Any change or the same? Take the stick out and put the other in. Reboot. Any change? If one works, one doesn't, you've found the culprit. Easy test to do and might save you some time.

---

### Post by wmichaelb2 on 2015-06-21
Bashing-om: Thank you so much for your prompt attention. I did as above, and got:

[CODE]ubuntu-studio@ubuntu-studio:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d56ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/mapper/ubuntu--studio--vg-root: 156.3 GB, 156292349952 bytes
255 heads, 63 sectors/track, 19001 cylinders, total 305258496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--studio--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--studio--vg-swap_1: 3489 MB, 3489660928 bytes
255 heads, 63 sectors/track, 424 cylinders, total 6815744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--studio--vg-swap_1 doesn't contain a valid partition table
ubuntu-studio@ubuntu-studio:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3bf08bdb-ee39-43f9-a9fc-638041466de4" TYPE="ext2" 
/dev/sda5: UUID="XcuVuc-epfh-MoDR-xbdS-gfrp-oCRB-t8Qlvc" TYPE="LVM2_member" 
/dev/sr0: LABEL="Ubuntu-Studio 14.04.1 LTS amd64" TYPE="iso9660" 
/dev/mapper/ubuntu--studio--vg-root: UUID="a8c68d7f-6fd2-4d81-83ac-14e109fce264" TYPE="ext4" 
/dev/mapper/ubuntu--studio--vg-swap_1:[CODE]

I read in the above "doesn't contain a valid partition table", which would certainly explain the
inability for the system to find the first block. Running GParted from the Hirem disk shows all the 
partitions as though they were perfect, but the system still won't boot. I was able to get the little
bit of data that I had on the system off, and I'm simply tempted to swap out the drive and start
over, unless you know of another tool to restore the partition table. 

Thanks again for your time!
they were perfect.

---

### Post by Bucky Ball on 2015-06-22
Thanks for using code tags. You appear to have left a / out of the final tag. See the last link in my signature. Thanks. :)

---

### Post by Bashing-om on 2015-06-22
wmichaelb2; Sorry;

LVM ( /dev/sda5 501760 312580095 156039168 8e Linux LVM) ; 
> 
 Disk /dev/mapper/ubuntu--studio--vg-root doesn't contain a valid partition table

is out of my sphere of experience. I do not know what to advise in this situatiom.

It might just be that you are encrypted and just that the swap partition is with an issue,
But, I do not know,
Perhaps others will respond and offer better advise.

[INDENT][INDENT]If I knew everything I would not be me
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-06-22
Yea, you have encrypted partitions by the looks. Can cause problems, and with /swap. Also out of my realm of experience so nothing more to add at this point except there is your starting point for research and hope someone LVM savvy will drop in.

---

### Post by wmichaelb2 on 2015-06-22
Thank you, folks. I'll take it from here.

---

### Post by Bucky Ball on 2015-06-23
If you need no more help on this thread, please mark it as solved to help others and start a new one for any further issues. Cheers and good luck. :)

---

