---
title: "partition/encription issue"
date: 2011-05-25
forum: Security
---

### Post by ABQskinhead on 2011-05-25
**SOLVED**
I'm not sure if this is the right place or not (too many possibilities), so I will post it here until I know otherwise. That being said... I use a notebook for work and require a secure place for files in case of theft. I had dev/sda6 for that purpose and I mounted it only when needed and it was encrypted with password.

Due to issues with file permissions:confused:, I had to re-install the OS. This time I do not have access to the dev/hda6 drive (owned as root) and get warnings when trying to unmount or encrypt it. I tried looking in the forums on the same issue, but I couldn't figure out how to correct it. If you don't mind helping, here is the info you need...

XXXXXX@XXXXXX:~$ sudo gedit /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext3    errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda6       /extra          ext3    defaults        0       2
/dev/sda5       /home           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=17e7788a-a0ac-4fc0-87a5-4f9f2540582d none            swap    sw              0       0


XXXXXX@XXXXXX:~$ sudo fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000736e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         125      999424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             125        2615    19999744   83  Linux
/dev/sda3            2615        3113     3999744   82  Linux swap / Solaris
/dev/sda4            3113       30402   219197441    5  Extended
/dev/sda5            3113       29779   214197266   83  Linux
/dev/sda6           29779       30402     4999168   83  Linux


XXXXXX@XXXXXX:~$ sudo blkid
/dev/sda3: UUID="17e7788a-a0ac-4fc0-87a5-4f9f2540582d" TYPE="swap" 
/dev/sda1: UUID="872961b8-9008-4d8e-b294-bd6bbe1433fa" TYPE="ext3" 
/dev/sda2: UUID="4b33c34d-9351-4f1c-b793-1aadb26753d4" TYPE="ext3" 
/dev/sda5: UUID="04808f0e-19a2-4bb7-bd86-d029fbca89da" TYPE="ext3" 
/dev/sda6: UUID="26ff86ea-11ed-4a91-a012-f687378916f5" TYPE="ext3" 

Thanks in advance :)

---

### Post by ABQskinhead on 2011-05-26
Ok, I figured it out. All I had to do was "#" comment out the /sda6 partition in the fstab file. I used the command "sudo gedit /etc/fstab" to achieve this. I then changed the partition ownership with "sudo nautilus" rebooted the system and mounted the partition manually. Using the Disk Utility I selected the option to reformat the /dev/sda6 partition. I selected the encryption button, entered a new pass-phrase and re-formatted the disk once again to enable the encryption. I can now mount and unmount manually and use that partition to secure my work. :D

---

