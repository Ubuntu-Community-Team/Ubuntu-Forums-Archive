---
title: "mdadm won't add additional device"
date: 2010-07-15
forum: Server Platforms
---

### Post by gencha on 2010-07-15
I'm trying to add an additional device to my md raid. I added a new disk to the system and created a new partition on it via fdisk.
When I try to add the disk to my array I get the following reply:
```

mdadm: add new device failed for /dev/sdh1 as 6: Invalid argument

```
syslog has more info:
```

Jul 15 21:58:15 dump kernel: [82152.469213] md: sdh1 does not have a valid v0.90 superblock, not importing!
Jul 15 21:58:15 dump kernel: [82152.469218] md: md_import_device returned -22

```
I find the error messages to be rather confusing. Of course the device has no superblock, it's brand new.
When I try to add the whole disc (as opposed to just the partition), it is added just fine.
So I assume something is wrong with my partition. So here is the fdisk output:
```

$ sudo fdisk -l /dev/sdh

Disk /dev/sdh: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bda07f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      182401  1465136001   83  Linux

```

---

