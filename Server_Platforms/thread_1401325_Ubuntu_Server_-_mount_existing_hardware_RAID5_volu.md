---
title: "Ubuntu Server - mount existing hardware RAID5 volume without formatting"
date: 2010-02-07
forum: Server Platforms
---

### Post by qx48 on 2010-02-07
First post in a couple years. 

I am currently trying to configure Ubuntu Server 8.04 LTS x86 to mount an existing NTFS hardware RAID 5 volume. I would like to do this without formatting the volume or having to re-create it. 

I am using an ASUS M2V-MX board with an AMD Athlon X2 Windsor 6000+ @ 3.0 GHz. 4 GB DDR2 memory, etc.

The RAID card I have is a Rosewill RC-209-EX with a Silicon Image SiI3114 chip. 

I have a volume already created with some data stored across the array.  There are 3x 500 GB Western Digital (green label) drives in the RAID5 setup. 

I am having trouble mounting it as a single volume. 
The "sudo fdisk -l" command indicates my 160GB installation drive as accurately defined. 

The other 3 drives, however are listed as seperate disks: 

/dev/sdb
/dev/sdc
/dev/sdd

... The /dev/sdb, and /deb/sdd drives each have a message saying that they "[don't] contain a valid partition table"... I'm assuming that this is because the /dev/sdc drive is the first one in rotation on my PCI card. 

I have read recently that a couple people have had success with Ubuntu automatically recognizing an array with this card. 

Not sure why this is happening. 

Any help would be greatly appreciated!

let me know if you need more information from me. 

Thanks! 
--Steve.

---

### Post by ian dobson on 2010-02-08
Hi,

Check if the "Silicon Image SiI3114" driver/kernel module is installed and loading. What does fdisk -l actually respond? Maybe your array is as /dev/raid or something like this rather than /dev/sd(bcd)

Sorry I can't say much more than this as I don't use/have a raid card.

Regards
Ian Dobson

---

### Post by tlsarles on 2010-02-08
I know that rosewell is a pretty low end brand. My guess would be that it's actually a soft RAID. I had done a RAID with an N-Force onboard RAID, which I had thought was a hard raid, as the RAID was defined in the BIOS, and Windows seemed to recognize it as a hard raid. However, I had the same issue trying to get it to work in Ubuntu, or any linux for that matter. Seems that it is more of a soft raid + Drivers to give it some hard raid functionality. A firm-RAID of sorts? I ended up selling the system, but if you get a solution, be sure to post it

---

### Post by qx48 on 2010-02-09
"sudo fdisk -l" output:


```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ec70ec6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris
/dev/sda3            5107       20023   119820802+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ae5758d

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
63 heads, 60 sectors/track, 258405 cylinders
Units = cylinders of 3780 * 512 = 1935360 bytes
Disk identifier: 0x6ae5758d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      516810   976769024    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

As far as Rosewill, I agree.
It looks like my card has some of the hardware RAID benefits like being able to boot from the array, etc., but offloads alot of the work onto the CPU. I figure this is why my card cost between $30 and $40 and not $600+...

As far as configuring the array, After the machine POSTs, but before grub loads, the Silicon Image boot sequence runs and gives me an option to edit its settings. This is where I created the array. I'm assuming this is similar to an onboard card being configured in the BIOS. 

Not sure how to check whether the driver/kernel module is loading. I didn't install the 3rd party drivers yet since Windows Server 03 recognized the array in Disk Management as a single volume without any special configuration. I will try to find an Ubuntu driver and post the results of the installation.

---

### Post by qx48 on 2010-02-09
Update: 

I couldn't find any drivers for this card for download other than the Windows ones. Everything I've read says that Ubuntu loads the drivers automatically, but the little documentation I see on these (Ubuntu) drivers' support for the RAID functionality of the card has come up with people having the same issue as I am and never figuring it out or having anyone follow up. 

I went back into the SiI RAID configuration after the BIOS, and it said the array was corrupt. So I went ahead and broke it and remade the array (I'll just have to transfer back all the data). "sudo fdisk -l" gives a slightly different output now, but it still only sees the seperate drives:

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ec70ec6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris
/dev/sda3            5107       20023   119820802+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

One may need to note that I haven't been able to format the array with a filesystem yet due to the fact that Ubuntu doesn't know that it is an array right now for some reason. 

I may just need to use straight up software RAID or switch the server back to Windows Server 2003. 

Not sure what to do yet, but if anyone ever figures something out, I would appreciate the information.

---

