---
title: "How to rebuild an existing RAID5 with newly installed Ubuntu Server"
date: 2010-10-06
forum: Server Platforms
---

### Post by MobileNet on 2010-10-06
Hi All

I have a Ubuntu Server system with OS running on a single 200GB primary hard disk, and software RAID5 created using  4x 2TB hard disk and mdadm. 

The RAID5 drive is used to store and share data across the network, and all OS related programs on the primary disk. 

The problem I have is I lost the OS disk. How can I rebuild the RAID5 after I re-install Ubuntu Server 10.04 (which is now installed on 2x 250GB HDDs with Soft-RAID1).

I had checked using fdisk, all RAID5 partition still exist on each hard disk.

Thanks

---

### Post by doogy2004 on 2010-10-07
Check out the man page at [http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)

try this command
```
mdadm --assemble --scan md-devices-and-options
```

---

