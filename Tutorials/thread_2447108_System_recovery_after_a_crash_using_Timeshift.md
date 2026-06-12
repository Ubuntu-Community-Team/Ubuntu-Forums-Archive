---
title: "System recovery after a crash using Timeshift"
date: 2020-07-12
forum: Tutorials
---

### Post by GhX6GZMB on 2020-07-12
Crashes happen, mostly from user incompetence (I mean me) and very rarely from hardware or software faults. Restoring a system to an earlier (functional) state is often not simple. The main problem is conflicts between UUIDs on a new install vs. the backup images, which make booting impossible. Here&#8216;s a recipe for solving this.

*This text presumes you have a Timeshift (rsync mode) backup snapshot created and available on external media. Only tested on Lubuntu 20.04LTS. Timeshift in rsync mode only works on ext4 file systems.*


**Scenario 1: User has changed/deleted/messed with something he/she shouldn&#8216;t have; system no longer boots. **

Live boot from DVD or USB drive and reinstall (x)ubuntu.
When getting to the partition settings, select &#8222;Manual partitioning&#8220;. Click on each partition, select &#8222;Edit&#8220; and set the mount points. _Under formatting select &#8222;Keep&#8220;!_
This will preserve the partition UUIDs.
Finish the install and reboot, reinstall Timeshift and restore the backup image.
Done.

[B]
Scenario 2: The disk is so messed up that the above doesn&#8216;t work, or the disk has  had to be replaced.[/B]

Live boot from DVD or USB drive and install (x)ubuntu.
When getting to the partition settings, select &#8222;Manual partitioning&#8220;. Create your partitions and mount points as they were before the crash (restoring will also restore the old fstab!) . Under formatting, select &#8222;Format&#8220; for each partition.
Finish the install and reboot, your partitions will now have new UUIDs.

Get the old UUIDs (on paper or print!) by inserting your Timeshift backup media and opening:
```
/media/<USER>/<mediaUUID>/timeshift/snapshots/<desiredsnapshot>/localhost/etc/fstab

```
Remove media.

Live boot again, open a terminal (ctrl+alt+T) and change the new UUIDs to the old ones using:
```
sudo e2fschk -f /dev/sd*xy*
sudo tune2fs /dev/sd*xy* -U *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee*

```For every partition.
sd*xy* is sda1, sda2, etc.
*aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* is the old UUID.
You'll not see the changes (using blkid) before next reboot, but don't worry, they're there.

Live boot and install (x)ubuntu once again, this time selecting &#8222;Keep&#8220; under formatting for all partitions. Don't forget to set the mount points again.
Install Timeshift and do your restore. Reboot and restore again to get the other users updated.
Done, your system should now be back to what it was before.


I&#8216;m fully aware that three live boots and two installs may sound over the top. But believe me, this is so little effort and time compared to searching for all instances and other implications of the partition UUIDs and setting them right. The (x)ubuntu installer does this so much better.


And it&#8216;s bullet-proof.

---

### Post by TheFu on 2020-07-13
And what do we do if we rework our storage completely?  Suppose we switch from ext4 to zfs or LVM+xfs or BTRFS?

---

### Post by GhX6GZMB on 2020-07-13
> **TheFu said:**
> And what do we do if we rework our storage completely?  Suppose we switch from ext4 to zfs or LVM+xfs or BTRFS?

The second sentence reads: "[COLOR=#000000]Restoring a system to an earlier (functional) state is often not simple." Did I phrase this badly?
[/COLOR]
Honestly: if you want to rework your system, do you really need a system backup? Seems a bit far-fetched to me. You'll want to restore /home, but that's a different story.

My HOWTO is for someone wanting the system back as it was before.

---

### Post by TheFu on 2020-07-13
There are multiple installation types that don't use UUIDs in the fstab.

My intention was only to get some assumptions or prerequisites added to the 1st post that only systems which mount using UUIDs will work this way and where the types of storage used are unchanged.  But for probably over 80% of normal desktop installs with EXT4 and EFI booting, this technique will probably work. Other file systems and legacy boot systems with a restore to a new HDD/SSD will probably fail.  Or did I miss something?

---

### Post by GhX6GZMB on 2020-07-13
Good point. But Timeshift in rsync mode only works with ext4 file systems.

---

