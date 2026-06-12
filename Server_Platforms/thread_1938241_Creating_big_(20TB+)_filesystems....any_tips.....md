---
title: "Creating big (20TB+) filesystems....any tips...."
date: 2012-03-09
forum: Server Platforms
---

### Post by ragtag on 2012-03-09
I'm trying to set up a 20TB share on a SAN using iscsi over 10GbE to connect to it. The iscsi, SAN setup, and all works fine, but I'm having issues with choosing a filesystem to use, and find tools that support this large a file system.

The two options I've been looking at are xfs and ext4. The server will be sharing the files out over NFS mostly (and Samba to a couple of users), and the files are big 500k to 16mb each and there is lots of them and there is quite a lot of read and write from aprox. 50 clients on 1GbE connections (more read than write).

What's the recommended approach for a setup like this?

I tried with ext4, but quickly bumped into the 16TB limits e2fstools in versions before 1.42-WIP...and I'm not sure if it's safe to use the development version of e2fstools for this.

I tried XFS, but it seems it combined with gpt made with parted caused the a missing superblock, after we crashed (disconnected the 10GbE cable) the raid. xfs_repair, was unable to find a superblock, and the whole raid was lost. Fine for testing, but not so cool once the raid is in production. I'm not 100% sure what happened here, which makes me a bit worried. I haven't tried using gfdisk instead of parted, it might do a better job of it.

I've also been considering adding a LVM, but I've never been a huge fan of them. I believe they reduce the performance a little bit, and add an extra layer of complexity, which means more things can go wrong. 

So what's the best approach when creating LARGE file systems, beyond 20TB, on Linux?

---

### Post by Habitual on 2012-03-09
> **ragtag said:**
> ...So what's the best approach when creating LARGE file systems, beyond 20TB, on Linux?


GlusterFS is an open source, distributed file system capable of scaling to several petabytes (actually, 72 brontobytes!)

---

### Post by drdos2006 on 2012-03-09
Hava a look here, uses ZFS for RAID.

[http://www.nexenta.com/corp/solutions/cloud](http://www.nexenta.com/corp/solutions/cloud)

regards

---

### Post by hawkmage on 2012-03-09
I would agree that ZFS is the way to go with a very large volume but the issue is that the ZFS license is not compatible with the Linux license so unless there is a change in the licensing you will not get ZFS as free a part of the Linux kernel.

BSD supports ZFS and some storage solutions built on it do so as well.  But many of those solutions can act as an iSCSI server bit not as a client.

---

### Post by matt_symes on 2012-03-09
Hi

> **hawkmage said:**
> I would agree that ZFS is the way to go with a very large volume but the issue is that the ZFS license is not compatible with the Linux license so unless there is a change in the licensing you will not get ZFS as free a part of the Linux kernel.

BSD supports ZFS and some storage solutions built on it do so as well.  But many of those solutions can act as an iSCSI server bit not as a client.

There is a port to Linux as well.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

As you say, it's not native in the kernel and i believe it requires FUSE. Not good for a boot partition then ?

Kind regards

---

### Post by hawkmage on 2012-03-09
FUSE in not good for a boot partition or anything else that that requires performance.  It is a user space filesystem driver and operated outside the kernel so it has to make freqent transitions between user and kernel mode operations to read/write so I wouldn't use it in a production environment

---

### Post by ragtag on 2012-03-09
Habitual: I've tested GlusterFS earlier, and it's very cool, but it doesn't fit what we're trying to do here...which is to mount one raid on a server.

ZFS is still at RC stages, and they say "That means that while the code is functional and stable it has not yet been blessed for 24/7 production usage." on their website. I know ZFS is good, but I need a system that runs 24/7 with high performance, so it looks like ZFS is out too.

I thought this would be a bit more straight forward. :( Maybe I need to look into gfdisk.

---

### Post by rubylaser on 2012-03-10
Personally, I use Solaris 11 (ZFS) + the napp-it web interface at home for one of my 2 fileservers.  zfsonlinux works well and is even bootable at this point, but if you're going to use it, I'd suggest using Solaris 11 or Openindiana with a pool version of 28, so it's portable to Linux, FreeBSD, or any Solaris based distribution.  Napp-it makes setup a breeze, and if you've ever tried GlusterFS, this is easier to use and troubleshoot imo.

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

### Post by matt_symes on 2012-03-10
Hi

> ZFS can be pretty darn fast

```
WRITE SPEED
root@solaris:~# dd if=/dev/zero of=/tank/documents/testfile.out bs=64k count=655360
655360+0 records in
655360+0 records out
42949672960 bytes (43 GB) copied, 137.527 s, 312 MB/s

READ SPEED
root@solaris:~# dd if=/tank/documents/testfile.out of=/dev/null bs=64k count=655360
655360+0 records in
655360+0 records out
42949672960 bytes (43 GB) copied, 70.4693 s, 609 MB/s
```


Thanks for these stats. 

Do you have any for ZFS under Linux ?

I have been thinking of migrating one of my servers to BSD to actually use ZFS.

Kind regards

---

### Post by rubylaser on 2012-03-11
I don't have the exact same setup with zfsonlinux or in FreeBSD, but all of the performance results I've seen from FreeBSD so far shows that it's fast, although not as fast as in Solaris / Openindiana.

---

