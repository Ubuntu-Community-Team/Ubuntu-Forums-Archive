---
title: "Need Help with Ubuntu server storage"
date: 2016-06-29
forum: Server Platforms
---

### Post by m1s3rys1gn4l on 2016-06-29
thats was my brother's ubuntu server, he ask me for upgrade it, then i have installed fresh copy of Ubuntu server 16
i am not a advance user of ubuntu server, n that was my mistake,
now i want to make something to server before it was,
it has installed apache2 with storage link,
i mean server contain 2+ hdd, i cant clearly told how much hdd, and all of hdd was in a group, and server has simple file server, 
like if i hit the server ip [http://182.48.xx.xx/storage](http://182.48.xx.xx/storage) then i can browse all of file from hdd,
someone told me what was that ? and how can i do this now ?

some of hdd details i have added bellow, :) and please dont mind about my english :(

```
root@smartnet:~# fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x8ecd6409


Device     Boot     Start        End    Sectors  Size Id Type
/dev/sda1  *         2048     249855     247808  121M 83 Linux
/dev/sda2          249856   62750719   62500864 29.8G 82 Linux swap / Solaris
/dev/sda4        62752766 2930276351 2867523586  1.3T  5 Extended
/dev/sda5       258064384 2930276351 2672211968  1.3T 8e Linux LVM
/dev/sda6        62752768  258064383  195311616 93.1G 83 Linux


Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.




Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xcb4a9bad


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2046 3907028991 3907026946  1.8T  5 Extended
/dev/sdb5        2048 3907028991 3907026944  1.8T 8e Linux LVM


Partition 1 does not start on physical sector boundary.




Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 91EFBCD5-AB68-4633-9DF1-F2E9E1D6E5FE


Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 5860532223 5860530176  2.7T Linux LVM








Disk /dev/mapper/group0-storage: 5.8 TiB, 6366173331456 bytes, 12433932288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

---

### Post by TheFu on 2016-06-30
Please post the output of:
* lsblk
* pvs
* vgs
* lvs

When using LVM to merge across HDD boundaries, it is best to ensure there is a backup for all storage before starting anything like an upgrade. I lost about 80% of all my data by merging storage across multiple drives without having perfect backups many years ago. Start with a simple backup.

Also, it would be helpful to remove all the "ram" stanzas above. They aren't helping, just confusing the main issue.  Also thank you very much for the "code tags". Huge help.

---

### Post by howefield on 2016-06-30
.. and moved to the "*Server Platforms*" forum.

---

### Post by m1s3rys1gn4l on 2016-06-30
> **TheFu said:**
> Please post the output of:
* lsblk
* pvs
* vgs
* lvs

When using LVM to merge across HDD boundaries, it is best to ensure there is a backup for all storage before starting anything like an upgrade. I lost about 80% of all my data by merging storage across multiple drives without having perfect backups many years ago. Start with a simple backup.

Also, it would be helpful to remove all the "ram" stanzas above. They aren't helping, just confusing the main issue.  Also thank you very much for the "code tags". Huge help.


```
root@smartnet:~# lsblk
NAME               MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                  8:0    0  1.4T  0 disk
&#9500;&#9472;sda1               8:1    0  121M  0 part
&#9500;&#9472;sda2               8:2    0 29.8G  0 part [SWAP]
&#9500;&#9472;sda4               8:4    0    1K  0 part
&#9500;&#9472;sda5               8:5    0  1.3T  0 part
&#9474; &#9492;&#9472;group0-storage 252:0    0  5.8T  0 lvm
&#9492;&#9472;sda6               8:6    0 93.1G  0 part /
sdb                  8:16   0  1.8T  0 disk
&#9500;&#9472;sdb1               8:17   0    1K  0 part
&#9492;&#9472;sdb5               8:21   0  1.8T  0 part
  &#9492;&#9472;group0-storage 252:0    0  5.8T  0 lvm
sdc                  8:32   0  2.7T  0 disk
&#9492;&#9472;sdc1               8:33   0  2.7T  0 part
  &#9492;&#9472;group0-storage 252:0    0  5.8T  0 lvm
sr0                 11:0    1 1024M  0 rom
root@smartnet:~# pvs
  PV         VG     Fmt  Attr PSize PFree
  /dev/sda5  group0 lvm2 a--  1.24t 2.77g
  /dev/sdb5  group0 lvm2 a--  1.82t    0
  /dev/sdc1  group0 lvm2 a--  2.73t    0
root@smartnet:~# vgs
  VG     #PV #LV #SN Attr   VSize VFree
  group0   3   1   0 wz--n- 5.79t 2.77g
root@smartnet:~# lvs
  LV      VG     Attr       LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  storage group0 -wi-a----- 5.79t



```

---

### Post by TheFu on 2016-06-30
&#9500;&#9472;sda2               8:2    0 29.8G  0 part [SWAP]

30G of swap?  Really? That is the largest swap I've ever seen for a personal server.
**free -mh** will show how much is used.  I bet less than 4G, if even that.  So you can probably reduce the size of that partition and ... and ... and that disks is sorta stuck - MBR partitioning makes it suck.  If it were GPT, you'd be able to shrink it, add another partition and add the new partition to the VG and extend the LV.

Hopefully, someone has told your brother that if **any one** of these disks fails, the data in the "storage" LV will all be lost, right?  I don't span disks with my LVs for that reason.  Burned myself once. Never again.  

The "storage" isn't the issue today. sda6 is the the problem.  I find it very hard to believe that 96G of OS and applications is even possible.  I'd bet there are media files or backups being stored on that partition - probably by accident. If it is a VM server, look for VMs under /var/lib/libvirt/ - and move those elsewhere.  Look for large files. I'd use **find** with the *-size +500M* option to see files larger than 500M.  

Good hunting.

---

### Post by m1s3rys1gn4l on 2016-06-30
ok can you tell me how can i browse the storage froup from sftp ? or can i make a apache2 file browser system ? or anything like simple file server ?

---

### Post by TheFu on 2016-06-30
> **m1s3rys1gn4l said:**
> ok can you tell me how can i browse the storage froup from sftp ? or can i make a apache2 file browser system ? or anything like simple file server ?

If ssh is already setup, then use any file browser with a URL like ssh://ip-to-system/.  That will get sftp to work. From Windows, use winscp.  sftp is considered secure even over the internet if ssh has been properly secured. DO NOT USE passwords, use keys. DO NOT ALLOW root to ssh in. There are a few other important things too.  If ssh isn't already setup, sftp won't work.

I cannot recommend **any** web-based file management. These are often non-secure and tend to be full of bugs and back doors. Plus they only work with apache's permissions, not your userid. WebDAV is an example.

But none of this will matter if you can't clean up the files filling /.  Using 'find' is the easiest way that I know.

---

