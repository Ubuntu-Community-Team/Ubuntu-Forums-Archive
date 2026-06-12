---
title: "Unbutu 16.04.3 LTS Large drive 10+TB."
date: 2017-12-28
forum: Server Platforms
---

### Post by torarneh on 2017-12-28
I created a large RAID5.
This is 16TB. (3x8TB drives)
The drive is found properly in VM etc.
But if i assign that drive to my Linux box.. it says (all 16TB gets assigned to the server)


root@ubuntu:/# fdisk -l
Disk /dev/sdb: 14,6 GiB, 15612206080 bytes, 30492590 sectors



[    2.622985] sd 2:0:0:0: [sda] 209715200 512-byte logical blocks: (107 GB/100 GiB)
[    2.627630] sd 2:0:1:0: [sdb] 30492590 512-byte logical blocks: (15.6 GB/14.5 GiB)


Any suggestions on what i need to do?

---

### Post by darkod on 2017-12-28
Yeah.

1. Don't use fdisk. fdisk doesn't work with gpt tables and you need that for any huge disks. Use parted instead.
2. The disk has to have gpt table, not msdos.

What does the following show:
```
parted /dev/sdb print
```

PS. Also, you are trying to assign a 16TB disk to a VM, right? You never mentioned which virtualization product you are using. You need to make sure it can support assigning 16TB storage to guest VMs.

---

### Post by torarneh on 2017-12-28
root@ubuntu:/# parted /dev/sdb print
Model: VMware Virtual disk (scsi)
Disk /dev/sdb: 15,6GB
Sektorstørrelse (logisk/fysisk): 512B/512B
Partisjonstabell: msdos
Disk Flags:


Number  Start  End  Size  Type  Filsystem  Flags

---

