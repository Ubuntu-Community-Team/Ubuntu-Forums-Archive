---
title: "iSCSI Target - Ubuntu 9.04"
date: 2009-07-11
forum: Server Platforms
---

### Post by johnbradbury on 2009-07-11
Hi Guys,
I'm setting up a new home lab for VMware ESX. As part of the new lab I've setup a new Ubuntu 9.04 host to act as a iSCSI target SAN. This has a 4TB RAID5 configuration (software) that I want to use as shared storage for all my ESX hosts.

I've installed the iSCSI target but now I;m stuck. How do I create LUNs on my RAID Array?

Do I need to format the array?

```

root@san01:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x430dd9f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7952597

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux RAID autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e9f30b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux RAID autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaaeaa6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux RAID autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028b2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux RAID autodetect

Disk /dev/md0: 3000.6 GB, 3000606523392 bytes
2 heads, 4 sectors/track, 732569952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by TJet1.8 on 2009-07-11
As much as I like Ubuntu, I don't know if I would you it to host iSCSI volumes.

Why don't you try Openfiler?

Openfiler is a free SAN, NAS, iSCSI, NFS, etc...utility based on Linux.
It has it's own confiuration GUI and works great for home labs.

Just go to openfiler.com and download it.

---

### Post by johnbradbury on 2009-07-11
I also need this host to act as a DNS server so I figured Ubuntu would be a good OS.

I've looked at OpenFiler but I had some problems creating a RAID configuration.

---

