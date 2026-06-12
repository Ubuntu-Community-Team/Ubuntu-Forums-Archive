---
title: "mdadm RAID1 setup recommendations"
date: 2008-06-05
forum: Server Platforms
---

### Post by robgolding63 on 2008-06-05
Hi,
I currently run a Windows Server 2003 box which hosts 3 virtual machines, it has 2.5G ram in total. I plan to install Ubuntu on this machine, to use as a VMware host instead of Windows - I have been told it will make a better host, and I would like to take advantage of mdadm software RAID.

I have done some testing and practicing with mdadm - and managed to setup a software RAID1 on a test server. My question is - what is the recommended procedure for setting up a RAID1 with mdadm?

On my test server, I first tried making a RAID1 array (/dev/md0) from the 2 disks - /dev/sdb and /dev/sdc. This worked, but I couldn't mount the disk afterwards - even after partitioning it. When making a partition with fdisk I ended up with /dev/md0p1, which gave an error of "Special device /dev/md0p1 does not exist" when trying to mount.

Then, I zeroed the superblocks and tried again. This time I partitioned the two disks first - giving /dev/sdb1 and /dev/sdc1, and then RAID'ed the 2 partitions - this gave a working array, which I first had to run **mke2fs /dev/md0** on to mount. However, I am now left with a partition called /dev/md0p1 when I do **fdisk -l**. Why is this? I am mounting /dev/md0 in /etc/fstab - so I don't know what this extra partition has to do with anything. I can't mount it, I get the special device does not exist message again. When running certain commands, I get funny errors about the partition not existing, even though everything is running fine - and the RAID is working as it should.

All I can think is that this is a remnant of the previous configuration. If so, how do I get rid of it? I don't mind ripping out the RAID again and trying again :).

Thanks a lot for any tips,

Rob

---

### Post by quelx on 2008-06-05
Just substitute *raid0* with *raid1*, the setup is fundamentally the same.

[http://ubuntuforums.org/showthread.php?t=807962](http://ubuntuforums.org/showthread.php?t=807962)

---

### Post by robgolding63 on 2008-06-05
Okay, I thought that might be the case. I started again, and did the following:

[LIST]
[*]Created partitions of type "fd" on 2 drives to be used
[*]Created RAID1 array with **mdadm --create /dev/md0 -l1 -n2 /dev/sdc1 /dev/sdd1**
[*]Used **fdisk /dev/md0** to create a partition of type "83" (linux) on new RAID array
Note: Here fdisk showed a new partition called md0p1, which I had never specified, but which must be the new "primary 1" partition.
[*]Used **mkfs -t ext3 /dev/md0** to format the new partition with ext3. (I tried /dev/md0p1, which would seem logical - but it gave an error, so I tried /dev/md0 and it worked, which seemed weird).
[/LIST]

And now the output of **fdisk -l** shows that /dev/md0 does not have a valid partition table (/dev/sdc and /dev/sdd still have their Linux RAID partitions).

However, the RAID array works perfectly. I can mount /dev/md0, and write to it. So what is this strange line in fdisk telling me?

Thanks for the help,

Rob

---

### Post by robgolding63 on 2008-06-06
I have just tried this exact same process on a Virtual Machine that I am using for testing, and I have got the same results. GParted shows that /dev/sdc and /dev/sdd have ext3 partitions on them, and /dev/md0 has a partition called /dev/md0p1, of which the filesystem is unknown.

However, as before the RAID is working perfectly. I am beginning to think this is normal behavior, as it has happened on two separate machines. Does anyone have a similar setup, so I can compare the output of **fdisk -l** and set up procedures?

Thanks a lot,

Rob

---

### Post by quelx on 2008-06-06
With **mdadm** you create one raid device for each partition.  For instance if you want */*, */home*, */var*, */boot* on different raid1 partitions

*/dev/sda* would be cut up into /dev/sda1, /dev/sda2, /dev/sda3, and /dev/sda4, all type fd, *Linux raid autodetect*, partitions.  /dev/sdb would be partitioned the exact same way.  A *md* device would be created for each partition, eg **mdadm -C /dev/md0 -l 1 -n 2 /dev/sda1 /dev/sdb1** for each device (raid partition):
```

/dev/sd{a,b}1 /dev/md0 /boot
/dev/sd{a,b}2 /dev/md1 /
/dev/sd{a,b}3 /dev/md2 /home
/dev/sd{a,b}4 /dev/md3 /var
```

md{0,1,2,3} act as partitions themselves and don't require further partitioning.  **mkfs** and any other partition level tools would be run on the *mdadm device* itself.

---

### Post by robgolding63 on 2008-06-06
> **quelx said:**
> 
md{0,1,2,3} act as partitions themselves and don't require further partitioning.  **mkfs** and any other partition level tools would be run on the *mdadm device* itself.

Okay, so once I've setup the RAID array, I should run mkfs on /dev/md0 -effectively skipping out the fdisk step, as /dev/md0 is already a patition?

I will try this now - I'm logged into my test server. So I'll remove the drives, stop the array, clean the config file, zero the superblocks and try again :).

Thanks a lot, I'll report back soon!

Rob

---

### Post by robgolding63 on 2008-06-06
Well I've just finished creating the array, and before I go any further I thought I should just quote the output of **fdisk -l**:

```

root@vhost-test:~# fdisk -l

[first disk omitted...]

Disk /dev/sdb: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa90162f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1245    10000431   fd  Linux raid autodetect

Disk /dev/sdc: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56eae429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         784     6297448+  fd  Linux raid autodetect

Disk /dev/md0: 6448 MB, 6448480256 bytes
2 heads, 4 sectors/track, 1574336 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

See how /dev/md0 is reported as a **disk**? Well I can't think what else it would be shown as - so I'm gonna go ahead and issue **mkfs -t ext3 /dev/md0** now, and see what happens :).

Rob

---

### Post by Titan8990 on 2008-06-06
I personally had implemented RAID1 via mdadm on an email server. After a couple days of fault testing the RAID1 configuration had failed every fault test except for one which was a test to replicate what would happen if a drive contained bad sectors and needed to rebuild.

I found that Ubuntu will not boot with only a single drive of the RAID1 configuration neither will it boot with one previous drive and another clean drive. If you can not boot in to the only OS that knows about your RAID1 configuration then how can you rebuild it?

In the end we bought a discrete RAID controller.

---

### Post by robgolding63 on 2008-06-06
The mkfs command seemed to be successful - but fdisk still reported md0 as having an invalid partition table - but GParted showed a partition called md0p1, ext3. That was good. To get fdisk to try and see it, I rebooted.

Just come back up now, and the array has disappeared. I forgot to populate the config file :(. I thought, however, that mdadm would pick up the array automatically without the config file. Obviously not.

Anyway, I added some info in the config file, told it to "assemble" the array, and added the 2nd disk back in (it had been removed for some reason).

Could anyone with a working, properly set-up RAID1 array, show me the output of **fdisk -l**. I'm not trying to boot from this array or anything, just use it as safe file-server storage.

Thanks,

Rob

---

### Post by Titan8990 on 2008-06-06
Should look something like this:

```
root@einstein:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005c03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29908   240235978+  fd  Linux raid autodetect
/dev/sda2           29909       30401     3960022+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1951

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29908   240235978+  fd  Linux raid autodetect
/dev/sdb2   *       29909       30401     3960022+  83  Linux

Disk /dev/md0: 246.0 GB, 246001565696 bytes
2 heads, 4 sectors/track, 60058976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

```

Edit note: This setup was not entirely correct as I had put /boot on a seperate partition than the RAID set. I had changed my RAID1 configuration a couple times before it was right and then I descided I didn't like it.

---

### Post by quelx on 2008-06-06
> **robgolding63 said:**
> Well I've just finished creating the array, and before I go any further I thought I should just quote the output of **fdisk -l**:

```

root@vhost-test:~# fdisk -l
..

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1245    10000431   fd  Linux raid autodetect
..
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         784     6297448+  fd  Linux raid autodetect

I could be wrong, but the array members must be the same size. So delete **/dev/sdb1** and create a new one which is *6297448* blocks in size.

EDIT: Don't worry about what **fdisk** is telling you about the *md* devices, both of my **mdadm** arrays show invalid partition tables, and I've been using them for months had drives fail and they kept trucking.

[CODE]Disk /dev/md0: 750.1 GB, 750169817088 bytes
2 heads, 4 sectors/track, 183146928 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

---

