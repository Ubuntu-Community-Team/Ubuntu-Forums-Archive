---
title: "Status of ZFS in Ubuntu Server"
date: 2014-03-28
forum: Server Platforms
---

### Post by sgofferj on 2014-03-28
Hi,

I have spent quite a bit of reading about storage in recent weeks and from what I have read, ZFS seems to be superior filesystem for storage servers, with not much but still clear advantages over BTRFS.
Could somebody comment on the *actual* current status of ZFS in Ubuntu Server? Is it production ready?

-S

---

### Post by lukeiamyourfather on 2014-03-28
Yes, XFS is production ready on Linux. The kernel has had XFS support for over a decade now and it's in use by many systems including many commercial NAS products. Depending on what you want to do there might be better options, not saying XFS is a bad option though because it's a great option in a lot of cases. Can you share specifics about the hardware and usage scenario you're considering?

---

### Post by sgofferj on 2014-03-28
Ahh, sorry, that was a short circuit in my brain. I meant to write ZFS, not XFS...

I'm in the process of remodeling my home server which used to have a 1TB Raid 1. Last year, both disks failed within a few days of each other. Luckily and thanks to the excellent Seagate Recovery Service, I got all my data back... As I said, I have been reading a lot in the last few weeks and from what I have read, ZFS (and BTRFS) are clearly superior to traditional RAID system with ZFS being a touch "better".
What I currently have in mind is 4x2, 4x3 or 4x4 TB in a RAID-Z2

---

### Post by thnewguy on 2014-03-29
Yes, ZFS is stable and works well on Ubuntu Server. I have been running a home file storage box with ZFS for over a year now and it has been a very good experience. It is surprisngly light on memory, my NAS has just 1GB of RAM and ZFS runs smoothly on it.

---

### Post by sgofferj on 2014-03-29
Great, thanks!

---

### Post by houstonbofh on 2014-03-29
And for the opposing viewpoint... :)

No it is NOT production ready.

1) You need a custom kernel.  ZFS can never be in the mainline kernel as the licensing is incompatible with Linux.  So you need a special kernel, and that means anytime something else goes wrong on the system, the kernel will have to PROVE it is not to blame.  (And it could be)

2) Dtrace - ZFS was developed on a system with dtrace, and it is key to troubleshooting and logging ZFS.  But it ain't on Linux for the same reason as ZFS.  Now there is a project that also has a patched kernel so it can be run.  And the kernel with two patches now is diverging further from mainline.

3) Maturity - ZFS is stable on Solaris and FreeBSd and has been for years.  It is designed to be stable and preserve data at all costs, and it has proven to do so.  The Linux project is still finding some rather surprising bugs that cause a loss of data, which is the entire reason ZFS came into being.

ZFS is very cool, and I love the file system!  It has some amazing features, and has bailed me out more than once!  I also love Linux!  But, if you want an enterprise ready file system, run ZFS on FreeBSD or Solaris.  (Note that nas4free and Freenas do this, and are easy to install appliances)  If you want to learn, develop and mess with things, run ZFS on Linux.

---

### Post by sgofferj on 2014-03-29
What's the way to go then on Linux? Btrfs? When it comes to my storage, I don't feel experimental...

---

### Post by nerdtron on 2014-03-29
> **sgofferj said:**
> What's the way to go then on Linux? Btrfs? When it comes to my storage, I don't feel experimental...

Depends on what data are you going to store? Database server? XFS is a good option.
Others, the default ext4 will get the job done.

---

### Post by sgofferj on 2014-03-30
Well, talking about redundant file storage, good RAID alternatives.

---

### Post by nerdtron on 2014-03-30
Are you concerned about performance issues?
Try RAID6 it guarantees you to support 2 drives failures. It's slower than RAID10 but at RAID10 can't survive 2 drives fails if they are on separate arrays.

And why rely on RAID for redundant file storage? Separate backups are invented for important data.

---

### Post by sgofferj on 2014-03-30
AFAIK, RAID6 needs more drives than RAIDZ2 for one thing. I can do RAIDZ2 with 4 drives. The other is that there is no terabyte backup-solution which would be affordable for private use besides disks, so my concept is a redundant system in the main server plus a NAS in a separate location for backups/snapshots/replication.
Then, backups - or restoring of them - mean downtime plus without any redundancy or integrity system, files might be corrupted without you even noticing it right away, so you might backup corrupted files and at some point you only have the corrupted version in your backup history. And Murphy says, you will need just that file, right when the last uncorrupted version is gone from your backup history.
So, IMHO, storing anything more important than /tmp on a plain disk without _*any*_ kind of redundancy or integrity check is plain stupid.

---

### Post by houstonbofh on 2014-03-30
If you want a separate NAS with a pile of disks, go with nas4free.  It is a FreeBSD based appliance that fully supports ZFS.  It is all open source, and yet enterprise ready.  I have used it with several clients.

And also, have a good offsite backup.  Backblaze is quite good.

---

### Post by CharlesA on 2014-03-30
> **sgofferj said:**
> AFAIK, RAID6 needs more drives than RAIDZ2 for one thing. I can do RAIDZ2 with 4 drives. The other is that there is no terabyte backup-solution which would be affordable for private use besides disks, so my concept is a redundant system in the main server plus a NAS in a separate location for backups/snapshots/replication.
Then, backups - or restoring of them - mean downtime plus without any redundancy or integrity system, files might be corrupted without you even noticing it right away, so you might backup corrupted files and at some point you only have the corrupted version in your backup history. And Murphy says, you will need just that file, right when the last uncorrupted version is gone from your backup history.
So, IMHO, storing anything more important than /tmp on a plain disk without _*any*_ kind of redundancy or integrity check is plain stupid.

RAID 6 still need a minimum of 4 drives just like RAIDZ2.

My current backup plan is to backup my NAS to external drives and sync to a backup array weekly. External drive backups are done daily. Works wonders and so far I haven't had issues with it.

---

### Post by sgofferj on 2014-03-30
> **houstonbofh said:**
> If you want a separate NAS with a pile of  disks, go with nas4free.  It is a FreeBSD based appliance that fully  supports ZFS.  It is all open source, and yet enterprise ready.  I have  used it with several clients.

And also, have a good offsite backup.  Backblaze is quite good.
There is no way in hell, my data leave my systems, let alone to some cloud-service abroad! Least of all to the US...

The NAS will be my "offsite-backup". As I wrote, main storage in the server and NAS in a different location (though still on the premises) and then replication. I was already planning for nas4free, hence my interest in ZFS for Linux, because if the server storage also runs ZFS, replication and snapshot handling should be less complicated.

---

### Post by thnewguy on 2014-03-30
> **houstonbofh said:**
> 
1) You need a custom kernel.  ZFS can never be in the mainline kernel as the licensing is incompatible with Linux.  So you need a special kernel, and that means anytime something else goes wrong on the system, the kernel will have to PROVE it is not to blame.  (And it could be)

2) Dtrace - ZFS was developed on a system with dtrace, and it is key to troubleshooting and logging ZFS.  But it ain't on Linux for the same reason as ZFS.  Now there is a project that also has a patched kernel so it can be run.  And the kernel with two patches now is diverging further from mainline.

3) Maturity - ZFS is stable on Solaris and FreeBSd and has been for years.  It is designed to be stable and preserve data at all costs, and it has proven to do so.  The Linux project is still finding some rather surprising bugs that cause a loss of data, which is the entire reason ZFS came into being.


1. This statement is entirely false. ZFS works just fine on a standard Linux kernel. The boxes I run with ZFS are using the default Ubuntu kernel.

2. Dtrace is only useful if you are going to develop ZFS, not use it. There is no need for Dtrace on a production or home system.

3. ZFS has been running smoothly on Linux for years. It is not as well integrated on Linux as it is on FreeBSD, PC-BSD and FreeNAS, but ZFS on Linux is entirely mature and stable.

---

### Post by houstonbofh on 2014-03-30
> **thnewguy said:**
> 1. This statement is entirely false. ZFS works just fine on a standard Linux kernel. The boxes I run with ZFS are using the default Ubuntu kernel.
So you are running it on fuse.

1) You can't boot like that.

2) I would not say that a user level storage driver is enterprise quality.

As for your other points, I think we have different definitions of "need" and "stable." That is OK, but it should be recognized.  For example, Friday I was replicating the only surviving copy of data valued at $2,000,000 USD.  One mistake or error on the consumer grade USB drive, and guess who gets the blame for loosing $2mil worth of data?  At that level you do not mess around.

And that is why we are talking about building two replicating NSA system in separate geographic locations.

---

### Post by sgofferj on 2014-03-31
@houstonbofh:
You pretty much got my point here, just that my data isn't worth millions but has high sentimental and also practical values. A few examples:
- All photos I ever took (I film-scanned all pre-digital era photos some time ago)
- All videos I ever took
- I changed from paper documents to a DMS some years ago, means, I scan every incoming document and discard the paper
--> Pretty much all documents regarding work and most regarding private life (except from a few IT certificates which are framed at my wall)

A lot of this data is currently spread over DVDs which I error-check-copy every once in a while, because big and reliable storage was out of my budget until now. The new system should finally get all data online available, which currently is close to 3TB and I'm thinking of 8TB netto capacity to have some room for the future (data is getting rather bigger than smaller nowadays).

So, data-safety (and security) is paramount for me.

> 1) You can't boot like that.

I at least didn't plan to boot from the storage array. I was planning to use a small SSD as system disk for the main server and nas4free anyways doesn't want to be installed on the storage array, so small SSD there too.

---

### Post by lukeiamyourfather on 2014-03-31
Lots of incorrect information in this thread about ZFS. I replied originally about XFS because that's what was there (edited to say ZFS after the fact). ZFS on Linux project is a port of ZFS that uses a kernel module instead of FUSE. The functionality missing that Solaris would've provided is provided through another kernel module called SPL (Solaris porting layer). These kernel modules run on whatever kernel you want to use, doesn't have to be a special kernel. ZFS on Linux is just as stable and reliable as ZFS on any other platform including FreeBSD because it uses the same code which is platform independent (since SPL handles the platform specific portions). It can also be used as a bootable root file system. ZFS on Linux is also production ready, is the Sequoia supercomputer at LLNL good enough to call it "production" ready? That's not to say it's perfect, but every software out there is a work in progress (even well established file systems like ext4 still have outstanding bugs that can result in loss of data, that's why you back things up). I have been using it in production on several machines with 36 disks (4TB disks, 384GB L2ARC, 128GB memory, 10GbE) and it has worked flawlessly. To the original poster, yes, I'd consider ZFS for your needs but of course it's not the only option.

---

### Post by lukeiamyourfather on 2014-03-31
Two things to add to this. The ext4 bug I was referring to is probably fixed by now, but this is what I was referring to. Always backup your stuff!

[http://www.phoronix.com/scan.php?page=news_item&px=MTIxNDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTIxNDQ)

The stable PPA for ZFS on Linux.

[https://launchpad.net/~zfs-native/+archive/stable](https://launchpad.net/~zfs-native/+archive/stable)

It's not difficult if you want to try it out. These commands will enable the PPA and install ZFS on Linux.

```

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get install ubuntu-zfs

```

Then you can create storage pools and file systems fairly easily. This example uses names from /dev/disk/by-id but there are other ways to specify disks. Or if you want to just mess around you can use files instead of disks (just for testing!).

```

sudo zpool create -f -o ashift=12 tank raidz2 ata-ST4000DM000-1F2168_W3005001 ata-ST4000DM000-1F2168_W3005002 ata-ST4000DM000-1F2168_W3005003 ata-ST4000DM000-1F2168_W3005004 ata-ST4000DM000-1F2168_W3005005 ata-ST4000DM000-1F2168_W3005006

```

This guide is very helpful!

[https://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/](https://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/)

---

### Post by sgofferj on 2014-03-31
Thanks! I'll start tinkering as soon as I have my new machine.

---

### Post by lukeiamyourfather on 2014-03-31
> **sgofferj said:**
> Thanks! I'll start tinkering as soon as I have my new machine.

Get ECC memory if you plan to use ZFS. A bit flip in memory could negate the data integrity features of ZFS (or any other file system for that matter).

---

### Post by sgofferj on 2014-03-31
Absolutely! I actually have a [hardware-thread]("http://ubuntuforums.org/showthread.php?t=2213770") open at the moment about my new server, because I haven't dealt with hardware for such a long time (and rarely did before) that I'm totally clueless in that aspect :D. I mean like which CPU with which board can do what, etc....
But ECC mem is pretty high on the list because a couple of weeks ago I spent hours searching for a problem which caused all kinds of services on my current server to segfault, and in the end, I found a few messed up cells in the highest DIMM... With ECC that wouldn't have happened or at least, the kernel would have screamed at me...

---

