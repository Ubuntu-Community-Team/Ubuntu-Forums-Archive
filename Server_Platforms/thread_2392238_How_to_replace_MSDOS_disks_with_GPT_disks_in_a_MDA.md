---
title: "How to replace MSDOS disks with GPT disks in a MDADM RAID10 Array"
date: 2018-05-18
forum: Server Platforms
---

### Post by m-dw on 2018-05-18
Hi

4 years ago I built a server with 4 x 2TB data disks in a RAID10 array formatted as EXT4. I am finally approaching 50% capacity (i.e. not really stretching the boundaries) but following a system disk failure and rebuilding on better hardware I think it might be time to replace the data drives. My case has hot-swappable SATA drive caddies so I need to stick with SATA rather than SAS (a decision I am happy with).

I'm currently looking at using 4 x 6TB SATA NAS drives. My plan is:
[LIST=1]
[*]back up data to an external drive.
[*]fail and remove drive 1.
[*]insert replacement drive 1.
[*]create GPT and RAID partition on new drive
[*]add new RAID partion to array and resync.
[*]repeat for 3 remaining drives
[*]reboot into single user
[*]umount /dev/md0
[*]use parted to increase partition sizes to use all available space.
[*]resize the filesystem on /dev/md0
[*]reboot into Ubuntu.
[/LIST]

Am I likely to run into problems with mixing GPT and MSDOS partition systems? What pitfalls might I encounter?


An alternative would be:
[LIST=1]
[*]backup data to en external drive
[*]update /etc/fstab.
[*]create new raid array with 4 new drives
[*]create file-system on new raid array
[*]restore data.
[/LIST]

If I was doing the second option, I would have more options (LVM, other file-systems), but I feel that this would be somehow more intrusive (several applications use/store data on the raid partition).

I would appreciate any advice you can offer.

---

### Post by rsteinmetz70112 on 2018-05-18
I am doing something similar with several machines using lvm2 over an mdadm array. 

I think either of your methods will work. I installed the new drives and used rsync to transfer the data since I was also changing the filesystem type. I had to temporarily install a SATA controller because I had more drives than the MB could handle. Once I transferred the data and got the drives configured I moved them around.

One problem I ran into was using lvm2 over mdadm on gpt drives is if the /boot directory is on a lv grub-install will fail. You can install grub2 on an lv in a mdos partition table. I started with gpt partitions but couldn't install grub2, fortunately I was able to simply change the partition table in gparted and the data was still there. I expected to have to rebuild the array. I wouldn't recommend trying that at home without a backup or at least a mirror in the array.   I was able to use gpt and msdos partitions in the same array.

Also you should actually create a partition on your drives. If you don't and try to use the raw drive with no partition it will work and some people recommend that but you can't install grub2 on the drives, since there isn't a place to put it. A default partition using the entire drive will leave some space at the beginning of the drive.

---

### Post by darkod on 2018-05-18
Why step 9? It is additional high risk and I don't think it's needed.

You now have array members of 2TB. You fail and remove one member, replace the disk, create 6TB array member and add it. mdadm will still treat it as 2TB useful size because the other member is only 2TB. You let the array resync.

After you have replaced all members, resize the md device and then the filesystem. Job done...

---

### Post by oldfred on 2018-05-18
Do not know LVM nor RAID.

But BIOS boot from gpt requires a bios_grub partition for grub to correctly install. It is 1 or 2MB unformatted with bios_grub flag or ef02 code if using gdisk.
Not sure with RAID, but expect it should be near where ever you have boot partition. They say bios_grub can be anywhere on drive, but then another entry said not further than 2TB into drive.

---

### Post by m-dw on 2018-05-19
Thank you all for your replies. To clarify, the RAID array contains only data. The system disk (which failed) is a single SSHD, and is backed up regularly to an external hard-disk (I wish I'd thought of that *before* the previous one died).

> **darkod said:**
> Why step 9? It is additional high risk and I don't think it's needed.

You now have array members of 2TB. You fail and remove one member, replace the disk, create 6TB array member and add it. mdadm will still treat it as 2TB useful size because the other member is only 2TB. You let the array resync.

After you have replaced all members, resize the md device and then the filesystem. Job done...

So you're saying that I can create a RAID partition to use the entire disk, and add it to the array? I wasn't aware of that, so thank you.

---

### Post by darkod on 2018-05-19
Correct. You can add partitions of various sizes to an array but they will all be used as if they had the size of the smallest one. However, adding a bigger partition from start saves you from needing to extend that partition later, so it lowers the risk of thing going bad.

Actually I just remembered one of my raid1 is made of 2TB and 3TB disks (after the original 2TB died it was replaced by 3TB). Here you can see the --examine output:
```
darko@file-srv:~$ sudo mdadm --examine /dev/sd[bc]3
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 61977668:b38d4847:03464c76:04961bab
           Name : file-srv:1  (local to host file-srv)
  Creation Time : Sat Oct  3 01:14:19 2015
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3839614976 (1830.87 GiB 1965.88 GB)
     Array Size : 1919807296 (1830.87 GiB 1965.88 GB)
  Used Dev Size : 3839614592 (1830.87 GiB 1965.88 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=384 sectors
          State : clean
    Device UUID : cfceaaee:2a94f35e:318d58f4:990f6e78

    Update Time : Sat May 19 12:31:18 2018
       Checksum : 8b5f758e - correct
         Events : 19471


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 61977668:b38d4847:03464c76:04961bab
           Name : file-srv:1  (local to host file-srv)
  Creation Time : Sat Oct  3 01:14:19 2015
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5793120256 (2762.38 GiB 2966.08 GB)
     Array Size : 1919807296 (1830.87 GiB 1965.88 GB)
  Used Dev Size : 3839614592 (1830.87 GiB 1965.88 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1953505664 sectors
          State : clean
    Device UUID : d45f5be7:10026ff5:fc18b3cc:86eaaf9c

    Update Time : Sat May 19 12:31:18 2018
       Checksum : 8b97fb34 - correct
         Events : 19471


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

As you can see the Used Dev Size and Array Size are the same for both partitions (2TB). But the Avail Dev Size of sdc3 is 3TB, because that partition is 3TB. If I replace the other disk with 3TB now I would be able to simply grow the Array Size to 3TB.

PS. When I said partition of various sizes I meant when creating an array the first time. If adding to already existing array the new partition has to be identical or bigger than the already existing array/partitions. But in your case that would be OK because you will be adding 6TB to 2TB array.

---

