---
title: "Cannot reboot Ubuntu server with active ZFS pool over ISCSI shared over Samba"
date: 2014-12-11
forum: Server Platforms
---

### Post by Kalle_Macklin on 2014-12-11
Hey everyone, we're building a NAS at work and we're having some trouble with ZFS on Ubuntu.

Ubuntu Server 14.04 on a i5 750 8GB Ram machine.
This machine has two NICs, one connecting to our network and the other to our VessRAID ISCSI device. The VessRAID has a bunch of hard drives in RAID. This array is connected via ISCSI to our Ubuntu server.

We chose to go with ZFS file system on the disk array. Following some basic tutorials we went through the following steps.
The steps are basically what's described here: [http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html](http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html)
With the difference that we don't create a mirror, just a pool. Also we don't do any samba stuff as per the tutorial - we know how to configure Samba and we made a share for the mounted folder and that works.

The steps we went through:

- Fresh install of Ubuntu Server
- Install ubuntu-zfs package 
- Created our zpool 'zfstest'
- Share via Samba

This works! Until we want to shut down or reboot the system.

The system hangs close to the SIGTERM and is locked up indefinitely after that.
No info whatsoever in system/kern logs about the shutdown/reboot hang. Things just stop.

After some troubleshooting, I figured out that if I 'zpool export zfsshare' before rebooting/shutting down, it works.
After more troubleshooting it seems to have to do with Samba. If I stop smbd before rebooting it can shut down properly.
I cannot manually 'zfs unmount zfstest' when smbd is running. So probably, the "K15zfs-share -> ../init.d/zfs-share*" rc0.d and rc6.d can't properly unmount either. Maybe.

When booting back up, the pool is not imported automatically.
We would like to get to the point where we can reboot the server and after reboot the ZFS pool is readily available and shared.

Any suggestions? Are we missing something crucial perhaps?

We're used to using 'service samba restart' and have it restart, but now it's 'service smbd restart' for example and that adds to our confusion.

---

### Post by biohazd on 2015-02-04
I have the same issue, looks like on shutdown it stops iSCSI before ZFS - which would then cause ZFS to hang.

Anyone have any ideas?

---

