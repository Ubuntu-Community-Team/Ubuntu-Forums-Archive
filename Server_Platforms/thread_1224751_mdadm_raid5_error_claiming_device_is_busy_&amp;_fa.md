---
title: "mdadm raid5 error claiming device is busy &amp; failing to find superblock as a result"
date: 2009-07-27
forum: Server Platforms
---

### Post by exploding5heep on 2009-07-27
I have been in the process of transfering data from an old raid5 to a new one I've put together. The process went well, until at the end I started having major issues. 

The raid is made up of 6 1TB drives, each one has 1 partition that is used for the raid. At first it worked fine, I could --assemble and mount, access data ok. After a restart one drive started reporting a

```
mdadm: cannot open device /dev/sdc1: Device or Resource busy
mdadm: /dev/sdc1 has no superblock - assembley aborted
```

This does not make sense to me. The device worked fine to begin with, nothing changed, and then it just stopped working. The /proc/mdstat file includes:

```
md_d2 : inactive sdc1[2](s)
              976759936 blocks
```

md2 is the raid device I'm trying to assemble. Why is sdc showing up in this odd way? All the --examines for the component drives return identical results. 

The worst part of this is that my first attempt to fix the problem was to remove the "failed" drive, start reformating it, and then try to run the array degraded. Doing this failed, because another drive started giving the same error. It assembled fine with the 5 drives, but gave an error when I tried to mount. Then after the restart the mdadm error came back. So now I have a 6 disk raid with 4 functional disks and 1 "problem" disk. 

To get to the point where this started happening, I grew the old raid by adding a 6th disk to the raid5 I had. I did the grow without issue. When I checked the filesystem with fsck.ext4 it gave an error about inode checksums not being correct, so I let it fix them all (every single one was wrong). After doing this it checked fine and said the filesystem was clean. I then grew the filesystem with no errors, and mounted it fine. I then restarted to install samba, and switched from ide to ahci on the drives, and the problems started when it booted up. All the drives still detect fine, so I don't see why ahci would be the problem. 

Any help would be appreciated. I would rather not lose all my data due to this.

EDIT: I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/27037") that discusses my problem. The loop workaround worked for me, and now the array is assembled in degraded mode. I just get the mount error now.

Did an fsck.ext4 and now everything is fine and working.

---

### Post by fjgaude on 2009-07-28
I guess I've never tried doing whatever folks do with **mdadm** to get the /dev/md_dx naming.

Using mdadm stright withoug doing any special has always worked for me. If you do things that it wasn't especially designed to do it usually ends up with busy devices, etc.

Glad you are learning whatever it takes to do things right.

---

