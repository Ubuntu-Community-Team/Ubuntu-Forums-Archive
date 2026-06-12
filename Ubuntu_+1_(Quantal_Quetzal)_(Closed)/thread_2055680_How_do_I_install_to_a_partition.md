---
title: "How do I install to a partition?"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by robtygart on 2012-09-09
[{Solved}]("http://ubuntuforums.org/showpost.php?p=12230602&postcount=12")
I am dual booting Kubuntu 12.04 and Ubuntu 12.04 I would like to switch my Ubuntu to 12.10.

Kubuntu is on sda1 and Ubuntu is on sda6. 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095350

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   159067399    79532676   83  Linux
/dev/sda2       159068158   312580095    76755969    5  Extended
/dev/sda5       308520960   312580095     2029568   82  Linux swap / Solaris
/dev/sda6       159068160   308520959    74726400   83  Linux

Partition table entries are not in disk order
```

I tried to run the Live USB, and chose the partition manager, then to install on sda6 but it gave me an error.

---

### Post by critin on 2012-09-10
What was the error?

---

### Post by kansasnoob on 2012-09-10
I get an error with the live images unless I press a key (generally enter) when the two small symbolic icons appear at the bottom of the screen.

If you immediately hit the enter key and then check disc integrity, rinse-n-repeat if the disc integrity passes OK, then choose to boot to live ................ then you should be OK.

---

### Post by mips on 2012-09-10
Have you tried updating ubiquity on the livecd maybe?

sudo apt-get update
sudo apt-get upgrade ubiquity

---

### Post by robtygart on 2012-09-10
Thanks! I will try it again.

Do I need to format the partition before installing?

---

### Post by dino99 on 2012-09-10
> **robtygart said:**
> Thanks! I will try it again.

Do I need to format the partition before installing?

Yes always format the / partition with the latest gparted or partedmagic (to get a clean partition).

---

### Post by GreatDanton on 2012-09-10
I always delete the partition before with Gparted live usb, however I think that even Ubuntu installer has option to format partition. You can try both.

---

### Post by robtygart on 2012-09-10
Here is what I did on the live CD installation..

Option: Something else (This shows a partition menu)

The top of the windows says "Installation Type"

I clicked sda6 and I edited it. it says "Use as" I choose ext4, I also clicked the format option.

on the bottom it says "Device for boot loader installation" I choose /dev/sda6.


The error I get says "No root file system is defined.    Please correct this from the Partitioning menu"

---

### Post by robtygart on 2012-09-10
I am going to go try and upgrade ubiquity, I had a bug report pop up the last time I tried to install 12.10.

---

### Post by ubername on 2012-09-10
Hi robtygart

Did you rememeber to set the mount point as  "/", as well as saying to use as ext4?

---

### Post by xebian on 2012-09-10
> **robtygart said:**
> Here is what I did on the live CD installation..

Option: Something else (This shows a partition menu)

The top of the windows says "Installation Type"

I clicked sda6 and I edited it. it says "Use as" I choose ext4, I also clicked the format option.

on the bottom it says "Device for boot loader installation" I choose /dev/sda6.


The error I get says "No root file system is defined.    Please correct this from the Partitioning menu"

Well, looks like you missed to select mount points.  Select "/" for the file system.

Also, for the boot loader, it's best to select /dev/sda for the master boot record.  Not /dev/sdaN as I find sometimes installer is flaky when installing boot loader to partitions instead of the master boot

---

### Post by jerrylamos on 2012-09-10
> **robtygart said:**
> Here is what I did on the live CD installation..

Option: Something else (This shows a partition menu)

The top of the windows says "Installation Type"

I clicked sda6 and I edited it. it says "Use as" I choose ext4, I also clicked the format option.

on the bottom it says "Device for boot loader installation" I choose /dev/sda6.


The error I get says "No root file system is defined.    Please correct this from the Partitioning menu"
Most always the boot loader goes on /dev/sda or /dev/sdb with no number behind it.  When you boot there is supposed to be a grub menu to choose which partition to boot that time.  You can use either /dev/sda or /dev/sdb I usually choose a or b to match where the install went to (with the number).

Below the format option there should be another set of options so choose "/"

---

### Post by robtygart on 2012-09-10
> **ubername said:**
> Hi robtygart

Did you rememeber to set the mount point as  "/", as well as saying to use as ext4?

xebian, Jerry.. :D Thank you it works!

---

