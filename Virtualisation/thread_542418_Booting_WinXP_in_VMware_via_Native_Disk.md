---
title: "Booting WinXP in VMware via Native Disk"
date: 2007-09-03
forum: Virtualisation
---

### Post by fogster on 2007-09-03
I've recently replaced my small WinXP-only hard drive with a much bigger drive. The primary OS is Ubuntu, but 'sda4' is a 60GB NTFS partition that's a clone of my Windows hard drive.

I never bothered trying to boot Windows from this, since Windows apparently doesn't like when it's not near the front of a disk. So the machine runs Ubuntu only; WinXP just sits there.

I'm trying VMware now, though, and am having some problems... I want to boot from that partition.

First of all, I'm running vmware as root to avoid permission issues.

I try to add a 'hard drive' to the VM as a 'physical disk' and set the partition (not a whole disk, but a partition) as /dev/sda4. I get the error:

```

Failed to load partitions for device /dev/sda4:
The partition table is invalid.
```

I then tried mounting sda4 via ntfsmount, but that didn't help anything so I unmounted it again. (I can mount it just fine, though, that way. It just doesn't help VMware any.)

I *think* the problem might have to do with a crappy partition job (logical vs. extended), but I'm able to mount and use /dev/sda4 fine otherwise, so I'm not so sure...

In case it matters...
```

**$ sudo fdisk /dev/sda**

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4863    39062016   83  Linux
/dev/sda2            4864        5112     2000092+  82  Linux swap / Solaris
/dev/sda3            5113       12407    58597087+   b  W95 FAT32
/dev/sda4           12408       19457    56629125    7  HPFS/NTFS
```

Can anyone at least tell me what's wrong? (Ideally, how to make it work...) Can I fix this without deleting partitions?

---

### Post by eb4fbz on 2007-12-04
I have the same problem, did u find any solution?

This is my fdisk:
```
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+   5  Extended
/dev/sda3           20525       25393    39110242+   7  HPFS/NTFS  <-- This is the XP partition
/dev/sda4           25394       30401    40226760    7  HPFS/NTFS
/dev/sda5            4864        5106     1951866   82  Linux swap / Solaris
```

I did a default ubuntu gutsy installation and after i did a dd from the old hard disk NTFS partitions to the end of the new one. I don't know why ubuntu created the swap in an extended partition:confused:

---

### Post by fogster on 2007-12-04
I did not find a solution. I lost interest and now have two computers. ;)

I think it has something to do with partitions being weird. I don't understand it in full.

---

### Post by gumbi18 on 2007-12-04
Fogster you must select both the Windows partition and the partition that Ubuntu is installed on. This is so that GRUB can load. Otherwise yes you will get a partition error because the Windows MBR is looking for GRUB but can't find it...

So when VMware server gives you the option of selecting partition's select:
/dev/sda1
and
/dev/sda4


Also check out my sticky for another method to booting existing Windows partitions.:)
[http://ubuntuforums.org/showthread.php?t=631671]("http://ubuntuforums.org/showthread.php?t=631671")

---

### Post by eb4fbz on 2007-12-08
I've found  a solution for our problem, this is what i did to fix it:

First i moved xp partition in table (not physical) to the second position, xp couldn't like to be after an extended partition. This is my fdisk -l /dev/sda after the operation:

```
/dev/sda1               1        4863    39062016   83  Linux
/dev/sda2   *       20525       25393    39110242+   7  HPFS/NTFS
/dev/sda3           25394       30401    40226760    7  HPFS/NTFS
/dev/sda4            4864       20524   125796982+   5  Extended
/dev/sda5            4864        5106     1951866   82  Linux swap / Solaris
/dev/sda6            5107       15405    82726686   83  Linux

Partition table entries are not in disk order
```

Now there is a problem. Becase we cloned the ntfs partitions to a different disk in a different position, start sector embedded in the ntfs filesystem don't agree it's new position, so we need to fix it manually:

First do a fdisk -ul /dev/sda to find the partition start sector:

```
/dev/sda1              63    78124094    39062016   83  Linux
/dev/sda2   *  [COLOR="Red"]** 329718060**[/COLOR]   407938544    39110242+   7  HPFS/NTFS
/dev/sda3       407938545   488392064    40226760    7  HPFS/NTFS
/dev/sda4        78124095   329718059   125796982+   5  Extended
/dev/sda5        78124158    82027889     1951866   82  Linux swap / Solaris
/dev/sda6        82027953   247481324    82726686   83  Linux

Partition table entries are not in disk order
```

Convert 329718060 to hex = 13A7192C
Swap the digits in pairs 13A7192C = 2C 19 A7 13

hexedit /dev/sda
Change the 4 bytes starting at 0x1C with the new starting sector number.
If you had the old xp in the beginning of the old disk, you will overwrite 3F 00 00 00 (63).
Exit hexedit saving changes with Ctrl+X

Edit boot.ini, originally:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
In my case i had to change partition numbers to:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition([COLOR="Red"]**2**[/COLOR])\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition([COLOR="Red"]**2**[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Now you should be able to boot that xp partition again from grub, my menu.lst entry is typical:
```
title     XP hd0,1
root          (hd0,1) 
savedefault
makeactive
chainloader +1
```

But booting it from vmware needs some tweaking, drivers cleaning and so, or you will get a BSOD. I'm working in this now, but that's another story.

This is a solution for fixing a cloned&moved ntfs partition, mystery solved, i hope it helps!

---

### Post by Jerrac on 2008-01-08
Did you ever get it working? I can get it to boot, but then I get a BSOD. I tried it by selecting my windows and linux partitions, windows, linux, and swap, and also the entire disk. Gave me a BSOD everytime right after the Windows XP logo appeared.

I also created a new hardware profile just for VMWARE.

---

### Post by Jerrac on 2008-01-08
Ok, figured it out. You need to install the scsi controllers inside of your xp install before you boot it in vmware. :D Now, just need to increase the video memory...

---

