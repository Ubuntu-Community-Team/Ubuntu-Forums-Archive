---
title: "TripleBoot: XP, Hoary and Breezy"
date: 2005-08-27
forum: The Cafe
---

### Post by Buffalo Soldier on 2005-08-27
Currently dualbooting XP-Hoary on my laptop (1 harddisk - 80Gb). Thinking of running adding Breezy.

```
10 GB - XP (ntfs)
 3 GB - DMZ - DeMilitarized Zone (vfat)
33 GB - Hoary (ext3)
 1 GB - Swap
33 GB - Breezy (ext3)
================
80 GB - Total
================
```

Anyone used to running a setup like this? Any problems that I should anticipate? JDong suggested that I have a seperate /boot partition... I guess that makes sense.

---

### Post by arnieboy on 2005-08-28
[QUOTE=Buffalo Soldier]Currently dualbooting XP-Hoary on my laptop (1 harddisk - 80Gb). Thinking of running adding Breezy.

```
10 GB - XP (ntfs)
 3 GB  - DMZ - DeMilitarized Zone (vfat)
33 GB - Hoary (ext3)
 1 GB  - Swap
33 GB - Breezy (ext3)
================
80 GB - Total
================
```

Anyone used to running a setup like this? Any problems that I should anticipate? JDong suggested that I have a seperate /boot partition... I guess that makes sense.[/QUOTE]
perfectly doable. goahead is what i wud say. I always have 3 or more OS's on my comp and ur partitioning is quite reasonable. having a /boot partition saves u a lot of headache later incase one of your OS's crashes.

---

### Post by manicka on 2005-08-28
I'm running this sort of setup right now with no problems.

---

### Post by benplaut on 2005-08-28
i recommend having a unified /home for breezy and hoary... i'm dual booting the two  :)

---

### Post by arnieboy on 2005-08-28
[QUOTE=benplaut]i recommend having a unified /home for breezy and hoary... i'm dual booting the two  :)[/QUOTE]
yes but just make sure u use two different user names when u boot into the two different systems.

---

### Post by Buffalo Soldier on 2005-08-28
Thanks for the feedback. Will give it a try. Downloading breezy iso now.

---

### Post by Buffalo Soldier on 2005-08-28
Which one did you guys install first? Breezy or Hoary?

---

### Post by aysiu on 2005-08-28
[QUOTE=Buffalo Soldier]Which one did you guys install first? Breezy or Hoary?[/QUOTE] I don't think it should matter, as long as they're on separate partitions.

---

### Post by benplaut on 2005-08-29
[QUOTE=arnieboy]yes but just make sure u use two different user names when u boot into the two different systems.[/QUOTE]

i didn't  :-# 

eh, not too many things broke  :roll:

---

### Post by arnieboy on 2005-08-29
[QUOTE=benplaut]i didn't  :-# 

eh, not too many things broke  :roll:[/QUOTE]
u mean u have the same user name and the same /home partition for both breezy and hoary?

---

### Post by manicka on 2005-08-29
[QUOTE=arnieboy]u mean u have the same user name and the same /home partition for both breezy and hoary?[/QUOTE]
 sounds like a recipe for disaster

---

### Post by Buffalo Soldier on 2005-09-05
Just would like to report triple booting working fine (so far). Installed Hoary then Breezy. Here are the details:

sudo fdisk -l output:```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        1640     2931862+   b  W95 FAT32
/dev/hda3            1641        1762      979965   82  Linux swap / Solaris
/dev/hda4            1763        9729    63994927+   5  Extended
/dev/hda5            1763        5744    31985383+  83  Linux
/dev/hda6            5745        9729    32009481   83  Linux
```

Breezy's fstab:```
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/dmz      vfat    defaults        0       0
/dev/hda5       /media/hoary    ext3    ro              0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Hoary's fstab:```
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /media/breezy   ext3    ro        	0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
```

Breezy's /boot/grub/menu.lst:```
default		0
timeout		10

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-8-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-8-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-8-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-8-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-8-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-8-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, kernel 2.6.10-5-386 (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, kernel 2.6.10-5-386 (recovery mode) (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, kernel memtest86+ (on /dev/hda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

