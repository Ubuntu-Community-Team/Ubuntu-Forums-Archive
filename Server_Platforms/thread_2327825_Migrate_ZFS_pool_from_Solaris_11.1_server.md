---
title: "Migrate ZFS pool from Solaris 11.1 server"
date: 2016-06-14
forum: Server Platforms
---

### Post by t.w.oliver on 2016-06-14
Hi all,

I currently run Solaris 11.1 in my home lab server. For a variety of reasons, I am wanting to switch over to Ubuntu server, especially now that ZFS is natively supported. I will use the same CPU/RAM/MoBo/OS SSD.

Ideally I'd like to move my zpool from Solaris to Ubuntu. From what I read this can probably be done with the zpool export/import commands.

However before I take the plunge, I'd like to understand if I am likely to have any issues or gottchas I should be looking out for.

- My zpool is version 34.
- I have 1 disk showing as degraded. Once I stand up Ubuntu I will put in some new disks, create a new zpool and copy my data over, then remove the degraded disk. Worried that import might fail with a degraded disk however.
- I have a l2arc and a logs partition on the same SSD that hosts the OS (i.e. 3 partitions). What effect will this have if they are destroyed when I move the zpool? I cant seem to find a good answer on this. I am assuming, because it is cache/logs, no real negative should happen.


My general thinking for the process is,
- export zpool
- shutdown server
- install Ubuntu on a new SSD (I might retire the hard working SSD that hosts Solaris)
- install and setup ZFS
- import existing zpool
- shutdown.
- connect new disks for new pool
- create new zpool with l2arc and logs partitions on new SSD
- copy data to new pool
- destroy the old pool and remove degraded disk


Any advice would be appreciated.
Thanks!!!

---

### Post by lukeiamyourfather on 2016-06-15
Oracle went to a closed development model starting with pool version 29. Only pool version 28 and lower can be transitioned to OpenZFS (or ZFS on Linux which is what Ubuntu is using).

[https://github.com/zfsonlinux/zfs/issues/1225#issuecomment-12576515](https://github.com/zfsonlinux/zfs/issues/1225#issuecomment-12576515)

---

### Post by t.w.oliver on 2016-06-15
Thanks for the heads up. Looks like I'm in a bit of trouble. Going to need to back up the pool somehow before moving over to ubuntu.

---

### Post by MAFoElffen on 2016-06-15
But... couldn't you define a new ZFS pool. Then move the data over to it? Even if it was to back the data off then restore to the new file system?

Just seems logical to me.

---

### Post by t.w.oliver on 2016-06-15
> **MAFoElffen said:**
> But... couldn't you define a new ZFS pool. Then move the data over to it? Even if it was to back the data off then restore to the new file system?

Just seems logical to me.

If I read that correctly, I think that would work if I were standing up a brand new Ubuntu server... create the new pool under ubuntu and do a file copy. In my case I am looking to reuse the hardware so once Ubuntu turns on, Solaris is gone and therefore the existing pool being unavailable.

Unless I misinterpreted your comment? Sorry.

---

### Post by MAFoElffen on 2016-06-16
But... My rule-of-thumb is that RAID or a pooled file system such as ZFS or LVM is not a backup. 

Before doing a major maintenance hrudle or a major upgrade, you always want to start out with a good backup so you have a fall-back point. A backup is data.

If you are migrating a filessystem or from one machine to another (in this case from one system to another, on the same hardware) your migrate the data from one to another, using an intermediate media (your backup). A backup does not have to be a system image. (in your case you just want the data on it, right?)

Even if you could convert the ZFS pools from one system to another, you wouldn't want to start attempting that without a backup.

Like I do now with RAID ... It's easier and faster to blow away a RAID array, redefine and assemble it, then write the data back to it from your backups, than to try to save, rebuild what you have and still chance not getting there. Server service is security, integrity and uptime. (When down, how long does it take to get back up to where you were.) Have a Recovery Plan.

You can pre-define ZFS pools and filesystems before installing 16.04 and it will see it. The modules are there now. It is not an option in the partitioner, but the partitioner on the install disk will see it if it is pre-existing. So if you re-create/re-define your ZFS onto the system, then you should be able to install with it in place. The you would just back-off your data back into your pools.

That just seems to be the easiest method to me. 

Sidenote: See attached pic, just to let you know that that is not just a shot in the dark... But it's still just one method of many.

EDIT:
Here's the 2 links I used for reference while testing it out myself, while Server 16.04 was in the Dev Cycle:
[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)
[https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-16.04-to-a-Native-ZFS-Root-Filesystem](https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-16.04-to-a-Native-ZFS-Root-Filesystem)

---

### Post by t.w.oliver on 2016-06-16
Thank you for the brilliant response. Much appreciated. I will absolutely take on your advice. 

Time to buy a backup drive :)

---

### Post by lukeiamyourfather on 2016-06-16
> **t.w.oliver said:**
> Time to buy a backup drive :)

When you transfer the files over to the new drive you can create a single drive pool with the new drive and use ZFS send/receive so you can keep snapshots and such just like any other ZFS pool. In Solaris create a pool specifically version 28 and you'll be able to read that backup drive with ZFS on Linux (Ubuntu). An example command for Solaris is below.

```
zpool create backup -o version=28 c3t0d0
```

---

