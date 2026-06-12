---
title: "Btrfs Problems"
date: 2012-02-26
forum: Server Platforms
---

### Post by ttshivers on 2012-02-26
I am having trouble with my RAID1 btrfs array. Here is some basic information about my system:
```
Linux server 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```A few days ago, my btrfs array stopped being able to be mounted after I rebooted one day. Here is the error I get when I try and mount the array:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```And dmesg says:
```
[49420.835709] device fsid 2c11a326-5630-484e-9f1d-9dab777a1028 devid 3 transid 43477 /dev/sdc
[49420.839514] btrfs: use lzo compression
[49420.839524] btrfs: enabling disk space caching
[49420.839531] btrfs: enabling inode map caching
[49420.855864] parent transid verify failed on 5568194695168 wanted 43477 found 43151
[49420.856324] parent transid verify failed on 5568194695168 wanted 43477 found 43151
[49420.856630] parent transid verify failed on 5568194695168 wanted 43477 found 43151
[49420.856637] parent transid verify failed on 5568194695168 wanted 43477 found 43151
[49420.858948] btrfs: open_ctree failed

```

---

### Post by ttshivers on 2012-02-27
I have also tried install a newer version of the Linux kernel. Also, here is some more information.
```

$ sudo btrfs-debug-tree /dev/sdh
couldn't open because of unsupported option features (8).
btrfs-debug-tree: disk-io.c:679: open_ctree_fd: Assertion `!(1)' failed.

```Btrfs-zero-log
```
$ sudo ./btrfs-zero-log /dev/sdh
parent transid verify failed on 5568194695168 wanted 43477 found 43151
parent transid verify failed on 5568194695168 wanted 43477 found 43151
parent transid verify failed on 5568194695168 wanted 43477 found 43151
parent transid verify failed on 5568194695168 wanted 43477 found 43151
Ignoring transid failure
parent transid verify failed on 5568194748416 wanted 43477 found 43151
parent transid verify failed on 5568194748416 wanted 43477 found 43151
parent transid verify failed on 5568194748416 wanted 43477 found 43151
parent transid verify failed on 5568194748416 wanted 43477 found 43151
Ignoring transid failure
parent transid verify failed on 5568195178496 wanted 43477 found 43151
parent transid verify failed on 5568195178496 wanted 43477 found 43151
parent transid verify failed on 5568195178496 wanted 43477 found 43151
parent transid verify failed on 5568195178496 wanted 43477 found 43151
Ignoring transid failure
```I have been unable to use btrfsck and I get this error when I try
```
$ sudo btrfsck /dev/sdh
couldn't open because of unsupported option features (8).
btrfsck: disk-io.c:679: open_ctree_fd: Assertion `!(1)' failed.

```

---

### Post by rubylaser on 2012-02-27
Have you tried using different btrfs superblocks for the fsck?

```
btrfsck -s 0 /dev/sdh
btrfsck -s 1 /dev/sdh
btrfsck -s 2 /dev/sdh
```

Sorry, I'm not a btrfs expert, so I won't be much help beyond this :)  I'm waiting for it to mature more before I trust my data to it.  I use either mdadm or ZFS for all my data.

---

### Post by redmk2 on 2012-02-27
> **ttshivers said:**
> I have also tried install a newer version of the Linux kernel. Also, here is some more information.
```

$ sudo btrfs-debug-tree /dev/sdh
couldn't open because of unsupported option features (8).
btrfs-debug-tree: disk-io.c:679: open_ctree_fd: Assertion `!(1)' failed.

```Btrfs-zero-log
```
$ sudo ./btrfs-zero-log /dev/sdh
parent transid verify failed on 5568194695168 wanted 43477 found 43151
parent transid verify failed on 5568194695168 wanted 43477 found 43151
parent transid verify failed on 5568194695168 wanted 43477 found 43151
parent transid verify failed on 5568194695168 wanted 43477 found 43151
Ignoring transid failure
parent transid verify failed on 5568194748416 wanted 43477 found 43151
parent transid verify failed on 5568194748416 wanted 43477 found 43151
parent transid verify failed on 5568194748416 wanted 43477 found 43151
parent transid verify failed on 5568194748416 wanted 43477 found 43151
Ignoring transid failure
parent transid verify failed on 5568195178496 wanted 43477 found 43151
parent transid verify failed on 5568195178496 wanted 43477 found 43151
parent transid verify failed on 5568195178496 wanted 43477 found 43151
parent transid verify failed on 5568195178496 wanted 43477 found 43151
Ignoring transid failure
```I have been unable to use btrfsck and I get this error when I try
```
$ sudo btrfsck /dev/sdh
couldn't open because of unsupported option features (8).
btrfsck: disk-io.c:679: open_ctree_fd: Assertion `!(1)' failed.

```

There is no working fsck for btrfs at the present.  See [***[COLOR="DarkSlateGray"]here[/COLOR]***]("http://lwn.net/Articles/462543/").  to my way of thinking: no fsck = no viable file system.  I'm with @rubylaser on this.  Use ZFS.

---

### Post by rubylaser on 2012-02-27
It looks like you're right, there is no working btrfsck at this point.  It appears like it's pretty [close to release]("http://www.phoronix.com/scan.php?page=news_item&px=MTA1OTQ").  But, Chris Mason has been promising this for a while.

Now that you can ZFS in Ubuntu natively, I just don't see the point of using btrfs until all it's parts are functional and well tested.

---

### Post by ttshivers on 2012-02-27
I will definitely switch back to zfs now. Is there any way to get the data off the corrupted volume?

---

### Post by ttshivers on 2012-02-27
Actually, I don't know what filesystem I will use now. I originally switched from ZFS to btrfs because of the enormous RAM requirements of ZFS. Any good filesystem suggestions for a RAID1 array consisting of 2 (2 TB) and 2 (500 GB) disks. Currently I have btrfs set up to make sure that there are 2 copies of a file on at least 2 different disks. I am not sure that any other filsystem does this type of RAID1.

---

### Post by rubylaser on 2012-02-28
Since there is no working btrfsck, the only thing I would suggest is sending a message to their message board, and see if you get any suggestions.  My guess is at this point, you're hosed until an fsck becomes available.  If you're not doing deduplication or encryption (you can't do this on a v28 pool like Ubuntu supports), you should be perfectly fine with 2GB of RAM.  How much RAM do you have in your machine? You can do the copies thing easily with ZFS like this
```
zfs set copies=2 rpool
```

Better yet, setup a backup to a different set of disks.  Multiple copies are great, but as you can see in the scenario you're currently in, even with 100 copies, if you can't mount the filesystem, your data is gone :(

---

### Post by ttshivers on 2012-02-28
This corruption just happened at a really bad time. A few days before the data became corrupted, I accidentally fried my backup disks when I accidentally put the power connector in backwards. This was just very bad timing. I normally am prepared for situations like this, but I never expected to lose my backup and main system at the same time.

As for another filesystem, I will look back into zfs. I originally switched to btrfs because of some of its very interesting features, such as copy on write and online defragmentation/balancing. Also, I was very much impressed with the benchmarking of btrfs compared to all the other filesystems. For me, btrfs has been at least 10 times faster (read and write) than my previous zfs filesystem. Even so, btrfs is still experimental and is lacking some key features such as a fsck. I will definitely look back into zfs while btrfs is still maturing.

---

### Post by arrrghhh on 2012-02-28
> **ttshivers said:**
> Also, I was very much impressed with the benchmarking of btrfs compared to all the other filesystems. For me, btrfs has been at least 10 times faster (read and write) than my previous zfs filesystem. Even so, btrfs is still experimental and is lacking some key features such as a fsck. I will definitely look back into zfs while btrfs is still maturing.

This ^^.

While BTRFS is promising, and in theory will replace ext... it's just not ready yet.

---

### Post by rubylaser on 2012-02-28
I'm looking forward to btrfs as well, but a filesystem without a working fsck really shouldn't even be considered.  Also, I'd really like RAID 5/6 support as well.

ZFS can be pretty darn fast :)  This is my backup server (9) 2TB disk array with 5,400 RPM drives in a raidz2 with 8GB of RAM and a very old AMD 4400+ X2 processor (load is at 10 when I did this, so my processor is the bottleneck).  This is much faster than my old (10) 1TB disk array with 7,200 RPM drives in an mdadm RAID6 on the same hardware which was around 250MB/s Read and Write.

```

**WRITE SPEED**
root@solaris:~# dd if=/dev/zero of=/tank/documents/testfile.out bs=64k count=655360
655360+0 records in
655360+0 records out
42949672960 bytes (43 GB) copied, 137.527 s, 312 MB/s

**READ SPEED**
root@solaris:~# dd if=/tank/documents/testfile.out of=/dev/null bs=64k count=655360
655360+0 records in
655360+0 records out
42949672960 bytes (43 GB) copied, 70.4693 s, 609 MB/s

```

---

### Post by ssam on 2012-02-29
have you tried booting with a newer kernel? btrfs is picking up bug fixes very fast as people find new ways to corrupt file systems. try getting the latest 3.3rc kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) (dont worry that it is labelled precise, it should work fine).

did you try asking on the btrfs mailing list? they seem to be interested in helping fix broken filesystems. or you could ask on their IRC.

there is almost/nearly a btrfsck [http://www.phoronix.com/scan.php?page=news_item&px=MTA2MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTA2MDI) but it is best to only use it if the devs advise you to.

---

### Post by Porcini M. on 2012-02-29
> **ssam said:**
> ...as people find new ways to corrupt file systems.

:lol:

---

