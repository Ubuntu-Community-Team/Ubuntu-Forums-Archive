---
title: "/dev/disk/by-id and usb connections"
date: 2015-06-23
forum: Ubuntu Development Version
---

### Post by sudodus on 2015-06-23
My SSD connected via a USB 3 and eSATA box (brand AKASA) is recognized differently by Wily compared to 14.04.2 LTS and other previous versions of Lubuntu (but it affects all Ubuntu family flavours).

When connected via USB 2 as well as USB 3 ports in the computer, [COLOR=#0000ff]Wily[/COLOR] will recognize it as an [COLOR=#0000ff]ata[/COLOR] drive as well as [COLOR=#0000ff]wwn[/COLOR] device (whatever that means).

When connected in the same way, [COLOR=#0000ff]14.04.2 LTS[/COLOR] and other previous versions will recognize it as a [COLOR=#0000ff]USB[/COLOR] device.

See the long 'code' list below with commands and output for both versions of Lubuntu.
```

lubuntu@lubuntu:~$ [COLOR=#0000ff]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily
lubuntu@lubuntu:~$ [COLOR=#0000ff]uname -a[/COLOR]
Linux lubuntu 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:14:22 UTC 2015 i686 i686 i686 GNU/Linux
lubuntu@lubuntu:~$ [COLOR=#0000ff]ls -l /dev/disk/by-id[/COLOR]
total 0
lrwxrwxrwx 1 root root  9 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159 -> ../../sdd
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part5 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part6 -> ../../sdd6
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part7 -> ../../sdd7
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part8 -> ../../sdd8
lrwxrwxrwx 1 root root 10 Jun 23 15:37 ata-KINGSTON_SV300S37A60G_50026B72510D8159-part9 -> ../../sdd9
lrwxrwxrwx 1 root root  9 Jun 23 15:21 ata-TSSTcorp_CDDVDW_SN-208AB_R8QJ6GFC90671R -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun 23 15:21 usb-SanDisk_Cruzer_Blade_200429068118F440A09E-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 23 15:21 usb-SanDisk_Cruzer_Blade_200429068118F440A09E-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jun 23 15:21 usb-SanDisk_Extreme_AA011223131538183687-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jun 23 15:21 usb-SanDisk_Extreme_AA011223131538183687-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Jun 23 15:21 usb-SanDisk_Extreme_AA011223131538183687-0:0-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 Jun 23 15:37 wwn-0x9320570021899030530x -> ../../sdd
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part5 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part6 -> ../../sdd6
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part7 -> ../../sdd7
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part8 -> ../../sdd8
lrwxrwxrwx 1 root root 10 Jun 23 15:37 wwn-0x9320570021899030530x-part9 -> ../../sdd9
lubuntu@lubuntu:~$ 
-----
lubuntu@lubuntu:~$ ###############################################################
lubuntu@lubuntu:~$ [COLOR=#0000ff]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
lubuntu@lubuntu:~$ [COLOR=#0000ff]uname -a[/COLOR]
Linux lubuntu 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686 i686 i686 GNU/Linux
lubuntu@lubuntu:~$ [COLOR=#0000ff]ls -l /dev/disk/by-id[/COLOR]
total 0
lrwxrwxrwx 1 root root  9 Jun 23 15:41 ata-TSSTcorp_CDDVDW_SN-208AB_R8QJ6GFC90671R -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-KINGSTON_SV300S37A60G_0000000001E1-0:0-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Jun 23 15:41 usb-SanDisk_Cruzer_Blade_200429068118F440A09E-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-SanDisk_Cruzer_Blade_200429068118F440A09E-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jun 23 15:41 usb-SanDisk_Extreme_AA011223131538183687-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-SanDisk_Extreme_AA011223131538183687-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Jun 23 15:41 usb-SanDisk_Extreme_AA011223131538183687-0:0-part2 -> ../../sdc2
lubuntu@lubuntu:~$ 

```

I think it can be an improvement, but it might also create surprises in software that is not 'aware' of the change :-P

Can ***you*** explain why and how this has been changed?

---

### Post by dino99 on 2015-06-23
maybe also use lspci to know how the ssd is named in both cases; anyway the wily way seems weird and needlessly confusing

---

### Post by sudodus on 2015-06-23
Do you mean ***lsusb***, where the following line is associated to the SSD in the external box?

in 14.04.2 LTS:
```
Bus 004 Device 003: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge
```

In Wily: the same, but different bus and device numbers.

---

