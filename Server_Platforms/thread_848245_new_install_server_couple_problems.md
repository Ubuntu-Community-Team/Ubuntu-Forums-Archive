---
title: "new install server couple problems"
date: 2008-07-03
forum: Server Platforms
---

### Post by kadafi69 on 2008-07-03
ok so ive just got a server set up with lamp and samba. few problems tho.

1) none of the hdds on the system are visible, when i first looked in fstab it was empty like so:

> # /etc/fstab: static file system information.
#
#<file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=76d7a41e-06a5-47de-b5f0-7ebdaf279d77 / ext3 relatime,errors=remount-ro 0
# /dev/sda6
UUID=f1560df0-dcf0-4d19-b756-8acbf81786da none  swap  sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


when i run fdisk -l i get this

> Disk /dev/sda: 160.0GB, 16004188569 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier:0x1780177f

Device  Boot       Start     End     Blocks    Id   System
/dev/sda1 *        1       19457   156288321    7   HPFS/NTFS

Disk /dev/sdb: 80.0GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57e179a7

Device  Boot       Start     End     Blocks    Id   System
/dev/sdb1 *         1       1058   8498353+     5   Extended
/dev/sdb2          1059     9729  69649807+     7   HFPS/NTFS
/dev/sdb5           1       1006   8080632     83   Linux
/dev/sdb6          1007     1058    417658     82   Linux swap / Solaris

Disk /dev/sdc: 250.GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier:0x080a0809

Device  Boot       Start     End     Blocks    Id   System
/dev/sdc1            1     30401  244196001     7   HPFS/NTFS

Disk /dev/sdd: 250.GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier:0x1cde373b

Device  Boot       Start     End     Blocks    Id   System
/dev/sdd             1     30401  244196001     7   HPFS/NTFS

there is also a startech PCI sata controller card which one of the hdds is connected to, i think its the 160gb.

2) I also want to make these hdds accessable from an xbox on the network.

3) im having some troubles with the localhost, none of the clients on the network can see [http://localhost/](http://localhost/)  it just comes up with the 'failed to connect error'

---

### Post by Titan8990 on 2008-07-03
It appears that you have installed Linux of logical partitions. I have heard of issues going along with that.

Only the local machine can view it's content via [http://localhost](http://localhost). All other machine will have to enter your ip address.

They could change with /etc/hosts list to show localhost as your server's IP address but that is highly not recommended.

---

