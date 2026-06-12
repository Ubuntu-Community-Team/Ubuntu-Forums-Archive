---
title: "Formattin NTFS into ext3 for XP installation in VirtualBox..."
date: 2009-05-28
forum: Virtualisation
---

### Post by vpnm_87 on 2009-05-28
my 

```
$ fdisk -l 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0680067f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        3824    15358108+   7  HPFS/NTFS
/dev/sda6            3825        6633    22563261    7  HPFS/NTFS
/dev/sda7            6634        6757      995998+  82  Linux swap/Solaris
/dev/sda8            6758        8216    11719386   83  Linux
/dev/sda9            8217        9729    12153141   83  Linux

```

attached snapshot of my system monitor window...

Now i want to install XP(or cteate some virtual drive) in /dev/sda1 which is 14.6 GB with HPFS/NTFS....
can someone kindly provide some help to achieve that?

BTW, Can anybody tell me what is that 68.3 MiB in my /dev/sda1?

---

### Post by vpnm_87 on 2009-06-03
I used Gparted and reformatted my first NTFS partition into ext3 partition...
Things went fine except some permission and owner problems..i guess now its fine:-)

But didnt try installing XP in that partiton using VirtualBox..moved my /home to separate partition and successfully installed XP in another partition

---

### Post by Chronon on 2009-06-03
A virtual disk is just a file on your host's file system.  You can have any format you like for the virtual filesystem.  If you want to virtualize XP then just mount the installation disk and install it to a blank virtual disk.

---

