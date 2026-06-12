---
title: "remove ubuntu chaletOS so no operating system"
date: 2019-06-10
forum: Ubuntu/Debian BASED
---

### Post by cascade992 on 2019-06-10
[COLOR=#26282A][FONT=&quot]hi there,

i want to remove ubuntu ChaletOS(thre are no other OS) so that it boots to bios. it's an HP eliteook 820 g1. I've found instructions for similar tasks but none that show how to remove it so that it boots to bios. i also want the harddrive completely erased. how would i do it?[/FONT][/COLOR]

---

### Post by TheFu on 2019-06-10
I have no idea how to boot to BIOS without banging on the BIOS setup key pre-boot.  Different computers use a different key for that F2, DEL, F12, ... F8 ... 

To wipe a HDD completely, I would boot from any linux install media - flash drive, dvd, cdrom, SDHC, whatever ... use the "Try Ubuntu" option.

If you really want to wipe everything so that only the NSA could recover it (or Israeli, Russian intelligence), then I'd use multiple passes running this command:
```
sudo ddrescue /dev/urandom /dev/sdZ /tmp/log
```
Leave that running overnight for the first pass.  You'll probably need to install ddrescue - this works with a temporary install.  /dev/sdZ needs to be the correct device. If you don't get the correct one, you can easily wipe the wrong device completely, including the device you used to boot into the "try ubuntu" environment.

How long it takes depends on the size of the disk and how fast it is.  An NVMe SSD will be faster than a SATA SSD, than a 7200 rpm spinning HDD, than a 5400 rpm spinning HDD, assuming they are all the same size.

/dev/sdZ is the entire HDD.
/dev/sdZ1 is the first partition on the HDD.
/dev/sdZ2 is the second partition on the HDD.
/dev/sdZ99 is the 99th partition on the HDD.

You can get the list of devices using **sudo fdisk -l**.  Use the size and vendor reported to map the correct device you want to wipe, i.e., sdZ.
 
There are lots of other ways to accomplish the same thing. Someone else might have a shorter method, like using D.B.A.N.  

If the disk was ever in a RAID, there are some other things necessary to clear the RAID bits, but it doesn't hold any actual data, just that is was used for "RAID" before.  It is a hassle to clear that data, but not worth getting into if no RAID was used.

---

### Post by oldfred on 2019-06-10
Newer drives have an ATA command using hdparm to erase.
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by cascade992 on 2019-06-10
thanks. it was originally a windows 8 OS but wasn't installed when i added chaletOS

---

