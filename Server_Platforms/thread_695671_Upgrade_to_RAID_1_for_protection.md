---
title: "Upgrade to RAID 1 for protection"
date: 2008-02-13
forum: Server Platforms
---

### Post by mikecrowe on 2008-02-13
Hi folks,

I have a production system that I'd like to move to RAID-1.  I have the 2nd hard drive installed, and am trying to gather what I need to do.

Right now, I have set up the second disk (mirroring the first partition sizes) as:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38208   306905728+  fd  Linux raid autodetect
/dev/sdb2           38209       38913     5662912+   5  Extended
/dev/sdb5           38209       38913     5662881   82  Linux swap / Solaris

```

Note:  /dev/sdb1 is formatted as ext3, since that's what the /dev/sda1 is right now.  Does that need to change?

Now, I need help getting from having my first disk configured as:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38208   306905728+  83  Linux
/dev/sda2           38209       38913     5662912+   5  Extended
/dev/sda5           38209       38913     5662881   82  Linux swap / Solaris

```

to ready for the following command:
> mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1

When I try to run the above, I get:
> mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=306905728K  mtime=Wed Dec 31 19:00:00 1969
mdadm: create aborted


which I'm sure means I need to boot off a live-CD and do, I know.  However, I'm concerned that I need to change partition types and such, which I don't know.

Can somebody give me the high level outline of what's next?

TIA
Mike

---

### Post by rickyjones on 2008-02-13
I do not know how to create RAID1 in a production system without data loss.

If you run that mdadm command and join the two drives you will LOSE all the data on the first disk if memory serves me right.

I would recommend creating a disk image of disk one, create the array, then image the backup back to the new RAID disk. That might accomplish the feat.

-Richard

---

### Post by ikonia on 2008-02-13
I wrote this guide in another thread a while ago

[http://ubuntuforums.org/showthread.php?t=454116&highlight=raid](http://ubuntuforums.org/showthread.php?t=454116&highlight=raid)

This walks you through it.

basiclly make a raid partition of the two disks you have but you mark you current system disk as failed (so a 2 disk array with 1 failed disk)

Copy your data onto the raid array of 1 disk and then boot off that raid array, then add the old system disk into the raid array (you can hot add) making you have a 2 disk raid array containing your system stuff and it's bootable.

don't forget to edit your fstab and grub config to point at the raid array devices rather than the raw disks.

---

