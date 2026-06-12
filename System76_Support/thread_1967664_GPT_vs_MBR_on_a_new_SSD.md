---
title: "GPT vs MBR on a new SSD"
date: 2012-04-28
forum: System76 Support
---

### Post by Balthazar_Droid on 2012-04-28
I will be installing a new SSD in my Wildebeast Preformance desktop in the next couple of days. My question is on formatting the drive. Should I use MS-DOS (which gparted uses by default) or GPT? Does it make any difference? Does the BIOS in my Wildebeast support GPT as it is shipped or do I need to change any settings in BIOS first?
Bios=WBIBX10J.86A.0293.2010.0419.1819
UEFI Boot is set to Disable (I'm guessing I need to at least enable this?)

---

### Post by oldfred on 2012-04-28
If you might install Windows you have to use MBR(msdos) unless you boot with UEFI. I have gpt with BIOS boot on my SSD.

But I hope to get a new UEFI system this summer and created the efi partition also. It is relatively small but does have to be first. With gpt you have to have a small 1MB bios_grub partition.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sde
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  10
```Arch recommends gpt for SSD:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.
The ef00 is the efi partition, the ef02 is the bios_grub partition and 04 is 12.04 and 10 is 11.10 soon to be 12.10.

---

### Post by isantop on 2012-04-30
On our systems, I recommend MBR, since that's what they're designed for by default. Since we use a BIOS instead of UEFI, there isn't a real advantage to choosing GPT, and it only creates issues later on.

---

