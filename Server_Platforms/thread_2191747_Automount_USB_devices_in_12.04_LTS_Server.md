---
title: "Automount USB devices in 12.04 LTS Server"
date: 2013-12-04
forum: Server Platforms
---

### Post by samuelrock on 2013-12-04
I have a media server that is made from an AllWell STB-6086  box. I have Ubuntu 12.04 LTS server "non PAE Kernel" installed on the  box.


  As of right now my storage media is composed of 4 1TB external USB  drives. I have a USB 2.0 PCI card installed that does not work until the  drivers for the OS are loaded.


  I attempted to put the disk drives UUID into the FSTAB but get a  error on boot as the drivers for the USB card loads after the FSTAB is  read.


  The drives are mixed format of ext3 NTFS and exFat. I am working on  moving all the formats over to ext3 for this project as the disk drives  will no longer be moved around.


  I need to know how to auto mount the USB drives once the drivers for the USB card is loaded. 
  I have searched to my wits end trying to solve this but no avail!


  Thanks for you help Sam

---

### Post by nerdtron on 2013-12-04
I think I'l' try this method:
"What is the command to mount the USB drive?"
Then add that command to the /etc/rc.local file and it will be executed at start up.

---

### Post by samuelrock on 2013-12-05
Ok, Ill try and let you know how it works!

Tks
Sam

---

### Post by samuelrock on 2013-12-05
Ok, It did not work. But here is why! I miss diagnosed the problem the first time! The system cannot see the drive upon reboot. I must disconnect and reconnect the drive in order for the system to see it.  So the reason your idea did not work is because there is no drive to mount :(

Copy of ssh log below.

Upon restart.> Last login: Thu Dec  5 04:01:05 2013 from ibm-t43
samuel@MediaServer:~$ sudo fdisk -l
[sudo] password for samuel:

Disk /dev/sda: 4017 MB, 4017807360 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7847280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cccfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     5750783     2874368   83  Linux
/dev/sda2         5752830     7845887     1046529    5  Extended
/dev/sda5         5752832     7845887     1046528   82  Linux swap / Solaris



Now I disconnect / reconnect the usb drive. > samuel@MediaServer:~$ sudo fdisk -l

Disk /dev/sda: 4017 MB, 4017807360 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7847280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cccfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     5750783     2874368   83  Linux
/dev/sda2         5752830     7845887     1046529    5  Extended
/dev/sda5         5752832     7845887     1046528   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953468416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fa52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953455804   976727871   83  Linux
samuel@MediaServer:~$ sudo mount -t ext3 /dev/sdb1 /media/movies
samuel@MediaServer:~$


Any idea how to fix this..  

OoO yea,, this happens with both the on board usb ports and the usb ports on the usb2.0 pci expansion card so I dont think its a driver issue as I did in my OP.

Sam

---

### Post by nerdtron on 2013-12-05
I saw this bug report. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364933)
Not 12.04 but I think it's worth a shot.
Edit your /etc/modules and add usb_storage on the last line

Reboot and you drive should be detected. And if you add it to your fstab, it should be mounted.

---

### Post by samuelrock on 2013-12-05
Sweet! 

I Added > usb_storage To the /etc/modules and it worked.. Drives now mount as per the FSTAB.

Thanks for your help
Sam

---

