---
title: "Software RAID CPU Usage"
date: 2009-07-16
forum: Server Platforms
---

### Post by zachtib on 2009-07-16
Anyone here using software raid on Ubuntu Server? I'm considering using software RAID1 on an Intel Atom 330 (Dual Core 1.6GHz) and want to get an idea of how well it'll work.

---

### Post by giggins on 2009-07-16
Never tried using software raid with an Atom processor... might be a little bit too much overhead for anything using striping, but RAID1 might not be too bad. I've used software RAID on several Ubuntu (and Debian) servers. Only thing to watch out with is make sure you label the physical drives appropriately when creating the mirror, because when one drive fails (and one will), you want to make sure you pull out the correct drive. Also, do a lot of reading up on mdadm's man page. Depending on your configuration, you may want to consider using LVM, because raid volumes only support one partition.

---

### Post by doogy2004 on 2009-07-16
> **zachtib said:**
> Anyone here using software raid on Ubuntu Server? I'm considering using software RAID1 on an Intel Atom 330 (Dual Core 1.6GHz) and want to get an idea of how well it'll work.

I'm runing RAID 5 on 2 ATA disks and 1 SCSI disk on a P3 330Mhz with 512MB of RAM. It works great for me, however when I'm doing alot of disk intensive processes the system will lock up for about 10-20 seconds till the RAID catches up, then everything works fine.  A faster processor would fix this problem, but it works for me.

---

### Post by zachtib on 2009-07-16
Thanks.

I'll look into using LVM, but at the moment, I'm only really planning on having a single / partition, unless someone wants to convince me otherwise.  But it sounds like the dual core 1.6GHz Atom should be able to handle the RAID without a problem, so it's looking good.

---

