---
title: "during server install, partitioner problem"
date: 2010-07-06
forum: Server Platforms
---

### Post by Skaperen on 2010-07-06
I am trying to make a replica server of an existing server on which I did install Ubuntu server 9.10.  I copied the partition table MBR sector from the first server over to the second server (did it running Ubuntu desktop trial mode).  Then I boot the Ubuntu Server CD.  Install is fine up to partitioning disks.  The partitioner won't show any of the existing partitions.  Attempts to select manual keep going between 2 menus.  It will try to make 2 partitions on the whole disk, replacing the existing table.  But that's not what I want.  I want the existing partition table to be used.  While installing other servers, I would get a list of existing partitions I could choose to use at this point.  Now, on this machine, I don't (same exact install CD as used on the others).  The disk does not seem to have any problems, as fdisk -lu /dev/sda will show the existing partitions just fine.  Someone knows what error it might be that confuses this partitioner?

---

### Post by stlsaint on 2010-07-06
are you using LVM? and you may have a corrupt disc.

---

