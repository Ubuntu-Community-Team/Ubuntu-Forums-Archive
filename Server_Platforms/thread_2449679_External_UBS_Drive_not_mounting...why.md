---
title: "External UBS Drive not mounting...why?"
date: 2020-08-31
forum: Server Platforms
---

### Post by lrzuniga on 2020-08-31
Have a QNAP DAS attached (USB) to a server running Ubuntu 18.04.5 which fails to mount at boot.


Server file system is BTRFS, the external drive is ext4.

Here is the /etc/fstab entry for the external drive.:
```
UUID=5b5cec0e-06f4-4120-bc65-39c1449c3d73   /qnapext    ext4    defaults,nofail     0   1
```
Odd thing is it wont mount manually to `**/qnapext**` but if I create another mount point like `**/qnapnew**` it will mount properly.

The next time the server reboots `**/qnapnew**` will fail to mount at boot or manually but if I create another mount like `**/qnapnew2**` it will mount properly.

What am I missing?

Here is the output of dmesg:

```
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Very big device. Trying to use READ CAPACITY(16).
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] 11720916992 512-byte logical blocks: (6.00 TB/5.46 TiB)
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] 4096-byte physical blocks
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Write Protect is off
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Mode Sense: 47 00 00 08
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Attached SCSI disk
```

Any help is appreciated.


Luis

---

### Post by TheFu on 2020-08-31
Normally, file systems are in partitions, not on the entire disk.  I would expect to see the partitions listed in the dmesg output.
If you can post all the commands and output necessary to create the fstab entry, maybe someone will see a problem?

I don't know anything about btrfs, sorry.

---

### Post by darkod on 2020-09-01
If I'm not mistaken, at least lsblk and blkid should list the drives/partitions/filesystem so you can also post that output to see if it helps:
```
lsblk
sudo blkid
```

I don't know QNAP so I assume this is only usb direct storage. Otherwise it might be better to consider connecting it as nfs over network (if possible).

---

### Post by lrzuniga on 2020-09-01
Thanks for the reply all, here are the outputs (the qnap external drive is connected via USB only and has not ethernet - its identifier is `/dev/sdg`):
[B]
lsblk:[/B]
```
NAME        MAJ:MIN RM  SIZE RO TYPE   MOUNTPOINTloop0         7:0    0   97M  1 loop   /snap/core/9665
loop1         7:1    0 96.6M  1 loop   /snap/core/9804
sda           8:0    0  931G  0 disk
&#9500;&#9472;sda1        8:1    0    1M  0 part
&#9492;&#9472;sda2        8:2    0  931G  0 part   /
sdb           8:16   0  1.8T  0 disk
&#9492;&#9472;sdb1        8:17   0  1.8T  0 part
  &#9492;&#9472;md0       9:0    0  9.1T  0 linear
    &#9492;&#9472;md0p1 259:0    0  9.1T  0 md     /archidata
sdc           8:32   0  1.8T  0 disk
&#9492;&#9472;sdc1        8:33   0  1.8T  0 part
  &#9492;&#9472;md0       9:0    0  9.1T  0 linear
    &#9492;&#9472;md0p1 259:0    0  9.1T  0 md     /archidata
sdd           8:48   0  1.8T  0 disk
&#9492;&#9472;sdd1        8:49   0  1.8T  0 part
  &#9492;&#9472;md0       9:0    0  9.1T  0 linear
    &#9492;&#9472;md0p1 259:0    0  9.1T  0 md     /archidata
sde           8:64   0  1.8T  0 disk
&#9492;&#9472;sde1        8:65   0  1.8T  0 part
  &#9492;&#9472;md0       9:0    0  9.1T  0 linear
    &#9492;&#9472;md0p1 259:0    0  9.1T  0 md     /archidata
sdf           8:80   0  1.8T  0 disk
&#9492;&#9472;sdf1        8:81   0  1.8T  0 part
  &#9492;&#9472;md0       9:0    0  9.1T  0 linear
    &#9492;&#9472;md0p1 259:0    0  9.1T  0 md     /archidata
**sdg           8:96   0  5.5T  0 disk   /qnapa**
```


**blkid:**
```
/dev/sda2: UUID="ccbbbac8-fa5a-11e8-b59e-d4ae526ce877" UUID_SUB="d95031f3-199e-41c6-b292-81985bef8957" TYPE="btrfs" PTTYPE="dos" PARTUUID="32eb0b93-7f46-49ba-81d1-5fdf83bc6b4d"/dev/sdb1: UUID="e3b40fc6-5b97-b845-72c0-6f53be8c5a26" UUID_SUB="4612c633-db60-2879-fa02-3fdb3400c50f" LABEL="archi:0" TYPE="linux_raid_member" PARTUUID="77074963-3949-470c-ae51-b6379dac02f1"
/dev/sdc1: UUID="e3b40fc6-5b97-b845-72c0-6f53be8c5a26" UUID_SUB="156a1428-27c9-d29d-4250-23152a9cae25" LABEL="archi:0" TYPE="linux_raid_member" PARTUUID="6091ccef-f200-46a3-9ff0-7b237388d0b7"
/dev/sdd1: UUID="e3b40fc6-5b97-b845-72c0-6f53be8c5a26" UUID_SUB="1e8ca5c2-5d76-c7c6-d5a2-0b1bbffab520" LABEL="archi:0" TYPE="linux_raid_member" PARTUUID="884f1617-35e8-47d8-a110-109f4d540fa8"
/dev/sde1: UUID="e3b40fc6-5b97-b845-72c0-6f53be8c5a26" UUID_SUB="270c4949-078d-e1cf-7994-28824820ba19" LABEL="archi:0" TYPE="linux_raid_member" PARTUUID="1e3529ae-9a79-456f-b9e0-f5f4936567cd"
/dev/sdf1: UUID="e3b40fc6-5b97-b845-72c0-6f53be8c5a26" UUID_SUB="b216b955-0bfc-ea31-2e9d-0d61f5e697d3" LABEL="archi:0" TYPE="linux_raid_member" PARTUUID="2aec41b5-3f0a-46c2-a075-98cc24b4a02a"
/dev/md0p1: UUID="c94c1597-258d-4990-8365-ecaa5aa21120" UUID_SUB="cbbb7e0c-25b1-408c-a6c6-e865d06a6d6f" TYPE="btrfs" PARTLABEL="archidata" PARTUUID="dd187daa-c06d-48bc-9079-7d24131c2b74"
**/dev/sdg: UUID="5b5cec0e-06f4-4120-bc65-39c1448c3d73" TYPE="ext4"**
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/sda1: PARTUUID="bb1d4f02-2bea-47ba-bb48-f1f24ebc9647"
/dev/md0: PTUUID="45a5f675-d60d-4d7e-ac29-d5cc2d60a530" PTTYPE="gpt"
```

**dmesg | grep /dev/sdg:**
```
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Very big device. Trying to use READ CAPACITY(16).[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] 11720916992 512-byte logical blocks: (6.00 TB/5.46 TiB)
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] 4096-byte physical blocks
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Write Protect is off
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Mode Sense: 47 00 00 08
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[Sat Aug 29 19:15:26 2020] sd 1:0:0:0: [sdg] Attached SCSI disk
[Sat Aug 29 19:19:16 2020] EXT4-fs (sdg): mounted filesystem with ordered data mode. Opts: (null)
[Sat Aug 29 19:43:52 2020] EXT4-fs (sdg): mounted filesystem with ordered data mode. Opts: (null)
```


Any help is appreciated.

L.

---

### Post by TheFu on 2020-09-01
```
UUID=5b5cec0e-06f4-4120-bc65-39c1448c3d73   /qnapext    ext4    defaults,nofail     0   **2**
```

Here's exactly what I use on a local disk here:
```
UUID=3ead5402-6bfd-479f-ad04-2bf3c7032119   /export    ext4 defaults,nofail 0  2
```

**sudo mkdir /qnapext** is needed before the mount should work. Can't mount to non-existing mount points.  I remember hearing that systemd.mount would create any directories needed.

So ... if that doesn't work, then I'd suspect that btrfs is interfering with the mount, but a quick search didn't find any mention of that as an issue. Maybe the CoW aspects of Btrfs is having a bad interactionThe lack of a partition is very troubling to me on a DAS.  Some programs demand there be a partition table.

Why use 2 and not 1 in the fstab? From the fstab manpage:
```
       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the order in
              which filesystem checks are done  at  boot  time.   The
              root filesystem should be specified with a fs_passno of
              1.  _Other filesystems should have  a  fs_passno  of  2._
              Filesystems  within  a  drive  will  be checked sequen&#8208;
              tially, but filesystems on  different  drives  will  be
              checked  at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to zero (don't fsck) if
              not present.
```

That's all I have.  How good are the backups for the DAS data? Putting a partition table (GPT) onto it is one of those few things that requires writing at the front and the end.  If the drive was shipped without a partition table, be certain to complain.

---

### Post by lrzuniga on 2020-09-01
Yup, I did create the `/qnapext` mount and it mounted ok manually. However on a reboot it did not. The odd thing is that after the reboot, it would not mount manually either.

So I created a different mount point `/qnapa` and confirmed it mounted manually ok. Modified /etc/fstab to point to the new mount and rebooted. It failed to mount AND then failed to mount manually...very odd.

So now, I have to create a new mount point after every reboot and mount manually to get access to the external drive...not a huge problem since I only use the external drive as cold storage.

I tried `2` in fstab sixth field since '0' and '1' did not work.

Not sure its a btrfs issue since the qnap device is a replacement for a consumer usb external drive that died...it mounted fine after every boot. 

Might be the qnap, which is RAID 1 of two disks.

I dunno

thanks for taking a look

---

### Post by TheFu on 2020-09-01
Perhaps a cheap, easy, experiment would be useful?

What if you format an 8G flash drive as ext4, no partition table, then mount it similarly using the fstab? Does that work?

If it doesn't, put a partition table on the 8G flash, create a partition, format as ext4, and mount using fstab.

If either or both of those tests work, then you have a clear indication what could be the root cause.

---

### Post by darkod on 2020-09-01
Like TheFu already mentioned, we can't see any partition on sdg. It looks like you formatted the disk directly, something you shouldn't do. I have never tried anything similar to be honest, and I don't know whether it can or can't produce these problems for you.

But if you still don't have too much data on this disk, I would move the data to temp location, create new blank gpt table on sdg (to get rid of the current filesystem), then create one big partition spanning whole sdg and then format that partition which would be sdg1.

Once you have that, you can start testing with mounting it. And then put the data back on it.

---

### Post by lrzuniga on 2020-09-01
@darkrod and @TheFu I think you are right. Formatting the disk directly was my mistake.

Is it possible to add the partition without disturbing the data already on the drive? I realize it's best to move the data off,  partition and then format, but the server is in a data centre and getting there is a bit of a hassle during covid.

But if I have to I have to.

thanks all for your collective brain power!

Luis

---

### Post by TheFu on 2020-09-01
> Formatting the disk directly was my mistake.
I did that too, once. Never again. Having a partition table is a recommended "best practice" for a number of reasons.

> Is it possible to add the partition without disturbing the data already on the drive? 
I don't see how. Sorry. 

But before doing that, I'd test the theory using a flash drive.

I've never heard of a production server that can be rebooted more than once a week, during approved, pre-scheduled, maintenance windows, usually at 4am Sundays.  Must be nice. ;)

---

### Post by lrzuniga on 2020-09-01
i'll do the test with another smaller drive, but Im sure it will work properly

The server is running archiware workstation backup so its not something end users see fail. and as you probably understand, getting these type of things fixed is an itch we just have to scratch  :P

---

### Post by darkod on 2020-09-01
There is no way to format and keep the data without moving it somewhere. But if you have enough free space on the server's internal storage for the data to fit, you might save yourself the trip to the DC.

You would do something like:
1. Create temp data folder on the internal storage.
2. Create temp mount point.
3. Mount the qnap to the temp mount point manually (you said it works the first time).
4. Once mounted copy the data from qnap to internal storage.
5. Unmount the qnap.
6. Put new blank gpt table on it and create one big partition. Format it.
7. Mount that partition and put the data back.

That is the only way I see. Even if you went to the DC you would still need to bring another temp storage where to move the data while you format the qnap.

---

### Post by TheFu on 2020-09-01
> **lrzuniga said:**
> i'll do the test with another smaller drive, but Im sure it will work properly

I am not. 

Suspect it could be an interaction between systemd.mount and brtfs and pretty much any mount.  We don't use btrfs due to reported issues with it and our normal deployment methods.  Of course, lots of people use btrfs without issues too.

systemd.mount has quietly replaced the fstab mount method used for 20+ yrs with few people noticing.  Sometimes, changes from that team are pushed out before they are production ready, I'm sorry to say. Some of the stuff is really good, but not all.

Another option is not to use the fstab for this mount at all, and try to use a systemd "unit" file for the mount.  [https://manpages.ubuntu.com/manpages/artful/man5/systemd.mount.5.html](https://manpages.ubuntu.com/manpages/artful/man5/systemd.mount.5.html)

---

### Post by lrzuniga on 2020-09-01
Thanks, sounds like a plan. I'll give it a try. fingers crossed!

---

### Post by lrzuniga on 2020-09-01
hmm..haven't heard of systemd.mount really, but then again, I am not a real sysadmin, more of an IT generalist.
Something to add to my "things to learn" list.

appreciate your time and sharing your knowledge.

---

