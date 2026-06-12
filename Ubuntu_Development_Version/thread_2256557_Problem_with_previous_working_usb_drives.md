---
title: "Problem with previous working usb drives"
date: 2014-12-13
forum: Ubuntu Development Version
---

### Post by edsloter on 2014-12-13
Windows recognizes, and opens this drive with no issues. I  tried it on another machine running crunchbang linux and it mounts and  opens with no issues. it looks like ubuntu thinks this is a usb camera?? it previously  recognized and I was able to use the drive before on this same ubuntu  machine, now it no longer works. 
  ```
dmesg | grep -i usb

```  results: [http://pastebin.com/Z1kXGAEf](http://pastebin.com/Z1kXGAEf)
  ```
ed@ed-X551MA:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub    
Bus 001 Device 003: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ed@ed-X551MA:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 927.1G  0 part /
&#9492;&#9472;sda3   8:3    0   3.9G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
ed@ed-X551MA:~$ sudo fdisk -l
[sudo] password for ed: 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't     
support GPT. Use GNU Parted.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
ed@ed-X551MA:~$        
      

```



[edit]

this is now an issue on multiple usb external hard drives, although thumb-drive types and card readers work just fine.

---

### Post by mc4man on 2014-12-13
Maybe file a bug on, which source ?, I'd go with either udev or udisks2
Here only see 2 issues concerning usb hdd's, 1 specific to vivid, one in general to at least 14.04 thru 15.04

The specific one is that a **usb 3 hdd** takes close to 35 sec.'s to become available in 15.04, in 14.04 the same drive takes about a sec. or 2 at most. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/140196](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/140196)

The in general bug is more disturbing - a **usb 3 hdd **cannot be powered off before detaching. It bothers me to have to power it down by yanking the usb cord out so won't be using in linux till they can treat properly, if ever. (windows does know how to power off these drives.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1401980](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1401980)

---

### Post by edsloter on 2014-12-13
ok. awaiting further development.

[https://answers.launchpad.net/ubuntu/+question/259045](https://answers.launchpad.net/ubuntu/+question/259045)
[http://askubuntu.com/questions/556447/ubuntu-not-seeing-external-usb-drive](http://askubuntu.com/questions/556447/ubuntu-not-seeing-external-usb-drive)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1402329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1402329)

---

### Post by mc4man on 2014-12-13
The only small issue here is generally this sub forum is for the dev, currently 15.04. Seems you're using 14.10?

---

