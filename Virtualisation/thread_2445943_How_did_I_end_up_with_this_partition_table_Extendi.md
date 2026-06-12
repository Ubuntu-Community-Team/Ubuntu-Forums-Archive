---
title: "How did I end up with this partition table? Extending a partition VM"
date: 2020-06-22
forum: Virtualisation
---

### Post by red1r on 2020-06-22
I just inherited this server (Ubuntu 18.04 LTS) and am confused as to how this happened and how to fix it. The server is in a VM using VMWare and the space was recently added 50GB. I thought it would be simpe enough to use parted to extend the partition but when printing the table this is what I see:

```
:~$ sudo parted /dev/sda
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
Model: VMware Virtual disk (scsi)
Disk /dev/sda: 53.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  12.9GB  12.9GB  primary   ext4            boot
 2      12.9GB  17.2GB  4314MB  extended
 5      12.9GB  17.2GB  4293MB  logical   linux-swap(v1)
```

How could partition 2 and 5 have the same start and end? And how would I go about expanding the partition 1 to the extent?

Regards.

---

### Post by Dennis N on 2020-06-22
I don't use VMware, but you likely made the virtual disk larger (53.7 GB)  without expanding a partition and file system, so total available remains at 17.2 GB. You need to find the commands to do that. Partition 2 is a extended partition in an MSDOS-partitioned disk and serves as a container for multiple logical partitions nested within it. You have one logical partition (5) taking up the entire range.

---

### Post by TheFu on 2020-06-22
sda2 is an extended primary partition. Only one is allowed per disk.
sda5 is a logical partition that fits inside.

Neither can be modified when mounted.   To modify them, you must make them unactive.

But none of that really matters, since sda5 is just swap and sda2 only holds the swap partition.  The easy way to solve many issue like this is to hook up a "Try Ubuntu" iso to the VM and boot from that.  Then use gparted to delete the sda5 and sda2 partitions, expand/resize the sda1 (though i would make it 25G and create 2 other primary partitions for /home and "swap"

But you get to choose what is best.

---

### Post by red1r on 2020-06-23
Thanks for the suggestions. I simply used cfdisk through a console and deleted the swap and extended partition then expanded the primary to 46G and recreated a swap partition of 4G. Then resized the partitions using resize2fs and now all good.

Regards.

---

### Post by slickymaster on 2020-06-23
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2020-06-23
> **red1r said:**
> Thanks for the suggestions. I simply used cfdisk through a console and deleted the swap and extended partition then expanded the primary to 46G and recreated a swap partition of 4G. Then resized the partitions using resize2fs and now all good.

Regards.

Glad you found a solution. Please mark the thread as "SOLVED" in the thread tools button to help the community.

---

