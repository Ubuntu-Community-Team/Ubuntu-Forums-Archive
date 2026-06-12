---
title: "Karmic disk image and LVM"
date: 2009-12-22
forum: Server Platforms
---

### Post by ezacon on 2009-12-22
I have a small server, with a fresh install of 9.10. During instalation, i have accepted defaults for partitioning, so i have LVM.
The server has only one 1Tb disk. I d'ont want 2 disks in mirror to preserve low power and noise.
I want an exact copy in an external disk. In case of disk faillure, i can replace it and boot.
I have copied the system disk with "dd if=/dev/sda of=/dev/sdb bs=64k".
In previous versions without LVM, i used to mount and rsync the copied disk to keep it up to date.
Now, with LVM, i cant mount the root partition of backup disk.
I know there are snapshots in LVM, but in this particular case, both volumes have same UUID.
If i connect both disks and do "vgscan" it detects the duplicated UUID.
I am new to LVM
How can i mount the backup disk and keep it syncronized?
here is the LVM config:
```

pvscan
  PV /dev/sda1   VG coll   lvm2 [931,27 GB / 44,00 MB free]
  Total: 1 [931,27 GB] / in use: 1 [931,27 GB] / in no VG: 0 [0   ]

vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "coll" using metadata type lvm2

lvscan
  ACTIVE            '/dev/coll/root' [908,69 GB] inherit
  ACTIVE            '/dev/coll/swap_1' [22,54 GB] inherit

fdisk -l /dev/sda
  Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
  255 cabezas, 63 sectores/pista, 121601 cilindros
  Unidades = cilindros de 16065 * 512 = 8225280 bytes
  Identificador de disco: 0x000e4289

  Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
  /dev/sda1   *           1      121570   976510993+  8e  Linux LVM
  /dev/sda2          121571      121601      249007+   5  Extendida
  /dev/sda5          121571      121601      248976   83  Linux



```

Thanks

---

### Post by ezacon on 2010-02-19
I finaly decided to migrate from LVM to normal disk partition.
LVM adds a level of complexity for recovery purposes.
In a backup disk, i have created same size partitions and trasfered files from /boot and root volume with rsync, presenving perms etc...
I have then modified /etc/fstab to mount new UUID's and reinstaled grub via live CD and chroot.

At this point, when i replace my system disk with backup one, the boot process start as usual, but when it starts loading services the boot process does not continue.
The system is not "frozen". If i press intro, there is a line feed on screen
If i mount the backup disk from another system, there is nothing writed to /var/log/syslog or dmesg files during the boot process.

¿any idea to trobleshoot this boot issue?

---

### Post by ezacon on 2010-02-19
Here are lasts relevant boot messages:
system disk:
```
....type 1505 audit.... operation="profile_load".....
.
.
Done.
Done.
 fsck from util-linux-ng 2.16
/dev/sda5: clean ......
fsck from util-linux-ng 2.16
 * Stopping remote control daemon(s): LIRC
 * Loading LIRC modules
 lircd-0.8.6[1057]: lircd(default) ready, using /var/run/lirc/litcd
/dev/mapper/coll-root: clean ......
 * could not access PID file for nmbd
 * Setting preliminary keumap...
 Ubuntu 9.10 coll tty1
 
 coll login:

```

And now the backup disk:

```
....type 1505 audit.... operation="profile_load".....
.
.
Done.
Done.
fsck from util-linux-ng 2.16
/dev/sda1: clean ......
fsck from util-linux-ng 2.16
/dev/sda5: clean ......
 * Stopping remote control daemon(s): LIRC
 * Loading LIRC modules
 lircd-0.8.6[1057]: lircd(default) ready, using /var/run/lirc/litcd
 * could not access PID file for nmbd
 * could not access PID file for nmbd
```

I can change with <alt>F2 but there is no login

Can a wrong swap partition or no swap partition at all produce this?
I have not initialized the swap partition. Is it needed to do something to a swap to use it?

Thanks

---

