---
title: "mdadm assembling raid incorrectly on boot"
date: 2011-05-24
forum: Server Platforms
---

### Post by FaeRhan on 2011-05-24
hi,

i'm using ubuntu 11.04 server edition. My mdadm raid5 array consists of 7 devices (sda1, sdb1, sdc1, sdd1, sde1, sdf1 and sdh1) and is working perfectly fine.

However, every time i reboot the system, the raid is assembled incorrectly, using sdh instead of sdh1. Obviously this doesn't work and it produces a huge error message when the system tries to auto mount the raid device on boot.
to fix that i have to manually remove sdh from the array, add sdh1 and let it rebuild everytime after booting.

anyone know of a way to fix this?

here is my mdadm.conf:

```
DEVICE /dev/sd[abcdefgh]1

ARRAY /dev/md0 metadata=0.90 level=raid5 UUID=e3efa909:3e3872a7:e4064135:44189116
```

---

### Post by psusi on 2011-05-24
Can you post the output of fdisk -lu?

---

### Post by FaeRhan on 2011-05-24
of course, here you go


```
sudo fdisk -lu

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064a25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930079284  1465039611   83  Linux

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000087b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  2930063219  1465031578+  83  Linux

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f00c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  2930079284  1465039611   83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1257

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  2930079284  1465039611   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6f76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  2930079284  1465039611   83  Linux

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d0b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  2930079284  1465039611   83  Linux

Disk /dev/sdg: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c6f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *        2048   136718335    68358144   83  Linux
/dev/sdg2       136718336   145225727     4253696   82  Linux swap / Solaris

Disk /dev/md0: 9001.2 GB, 9001153462272 bytes
2 heads, 4 sectors/track, -2097420064 cylinders, total 17580377856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 393216 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdh: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6414706

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  2930272064  1465136001   83  Linux

```

---

### Post by dtfinch on 2011-05-24
Did you run update-initramfs (probably at least "update-initramfs -u", or "update-initramfs -c -k all" to be more thorough) after you updated the device line in your mdadm.conf?

---

### Post by FaeRhan on 2011-05-24
> **dtfinch said:**
> Did you run update-initramfs (probably at least "update-initramfs -u", or "update-initramfs -c -k all" to be more thorough) after you updated the device line in your mdadm.conf?
nope, gonna try that, thanks ;)

edit: yes! that did it, thanks man :)

---

