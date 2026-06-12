---
title: "Max drive size?"
date: 2010-10-08
forum: Server Platforms
---

### Post by bcdudley on 2010-10-08
I just built a new 10.04 server. It has a 500Gb drive for the operating system and a 22 Terabyte drive that will be used for data.  When I format the data partition, it only shows 2.2Tb available. I have this formatted as ext4. I know there is a 16Tb limit and I am going to repartition my drives, but shouldn't I at least be seeing 16Tb instead of 2.2.

Thanks.

---

### Post by Cosma on 2010-10-08
you need to use gpt disk lables to make partitions bigger than 2TB (you have to use parted for this)

---

### Post by bcdudley on 2010-10-08
Thank you.

---

### Post by srs5694 on 2010-10-08
You can also use my [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) or various non-Linux tools, for GPT partitioning. (I think FreeBSD's gpt tool has been ported to Linux, although AFAIK it's not available in the Ubuntu repositories.)

The ext4 filesystem size limit is not 16 TiB; it's 1 EiB (at least, according to [Wikipedia](http://en.wikipedia.org/wiki/Ext4fs)). There is a 16 TiB limit in ext4fs, but it relates to individual files, not the filesystem as a whole. The ext3fs limits are much lower. Its maximum partition size is 2-16 TiB, depending on values set at filesystem creation time; and its maximum file size is 16 GiB to 2 TiB. (Again, according to [Wikipedia.](http://en.wikipedia.org/wiki/Ext3)

XFS and JFS are also options for large-filesystem support. So is Btrfs, if you're willing to live on the edge. (It's still officially experimental.) Personally, I'd use XFS for a really big filesystem. It's been around for a long time, and even on Linux it's got a longer track record than ext4fs. I've seen very few complaints about XFS on Linux. JFS was slower to stabilize on Linux than XFS, and I've had occasional problems with it when I push it hard in tests even recently. IMHO, the main drawback to XFS is that it can't be shrunk, which can make reorganizing your filesystems tricky in some situations. Perhaps in another year Btrfs would be worth using; it's got some very advanced features, like snapshot support, but it's still too new to be recommended, IMHO.

---

### Post by gordintoronto on 2010-10-08
Nobody sells a 22 TB drive this year. What do you actually have?

The biggest drive you can buy is 3 TB.

---

### Post by srs5694 on 2010-10-09
It's possible to build RAID arrays that are pretty huge. I don't know offhand what the top theoretical limit is, but I'd bet it's well above 22 TB.

---

### Post by ian dobson on 2010-10-09
Hi,

I think the maximum file size you can create for ext4 is 16petabytes. I think a GPT partition can be 1petabyte. So you've got a long way to go until you hit one of these limits.

EDIT: looks as if a gpt partition can be 9 Zettabytes ([http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)). and ext4 file system can be 1 EB ([http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4))
Regards
Ian Dobson

---

### Post by gordintoronto on 2010-10-09
> **srs5694 said:**
> It's possible to build RAID arrays that are pretty huge. I don't know offhand what the top theoretical limit is, but I'd bet it's well above 22 TB.

Using hard drives which are available today, you could (barely) reach 22 TB, with a box which can hold 10 drives and the very latest drives.

However, if the "drive" is a RAID array, it would be extremely relevant to the question at hand, and the OP has not indicated that it is a RAID array.

---

### Post by bcdudley on 2010-10-11
It is a raid array. I have a 3Ware 9550SXU-16ML Raid card. It is a 16 port raid card made by LSI. I am running 3 x 250Gb in raid 5 with a single 250gb as a hotspare. The remaining 12 drives are occupied by 2Tb drives in a raid 5 configuration. 

With the drives acting as a single unit, it comes out to just over 20Tb actually. 

Over the weekend, I partitioned the drives down to 2 x 10Tb partitions. I have not checked it yet this morning to see the results.


Edit: Using a parted magic live cd, I was able to correctly partition the drive as needed. Thank you everyone for the help.

---

