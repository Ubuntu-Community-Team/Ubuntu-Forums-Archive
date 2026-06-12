---
title: "Scheduled backups"
date: 2015-06-15
forum: Security
---

### Post by Iznougoud on 2015-06-15
Installation: Ubuntu Server 14.04 (headless) running 24/7.

Being in the process of recovering from a failed HDD, I've decided to do things properly this time around. That is, I am going to create backups on a regular basis - in some cases even on a daily basis. That's my ambition, this is my problem:

The partitions to be backed up are on /dev/sda - sda1, sda2, sda3 and sda4. sda1 is a BIOS-partition (the disk being converted from MBR to GPT, my guess is that should I recover the partition to a GPT-partitioned disk, I won't need to include sda1. Correct me if I'm wrong) and consequently not a filesystem as such. sda3 is a swap-partition, and for obvious reasons not vital to backup. That leaves us with sda2 (the boot-partition) and sda4 (the storage facility for documents photos and such. Partition sizes being 220Gb and 2.7Tb respectively, although they're nowhere near that amount of data at this point or in the near future.

rSync will do the job for /dev/sda4. I will only need to backup a small number of specified directiores such as documents, photos and so on. This can easily be done several times a day, once the initial backup has been made.

When it comes to /dev/sda2, however, rSync simply won't do. For a number of reasons, one being that I have a number of binds to (large) directories on the other partition, and I need to have as complete a copy of the partition as possible to restore it as a bootable device. This is why a disk image seems the best way to go. Clonezilla would do the job, but not on a schedule (unless you put dates in your calendar, boot down and manually back it up on those dates), so I thought I'd use dd via CRON. As it turns out, or at least as I understand it, dd also needs the systems partition to be unmounted in order to make a proper recoverable image. Which simply isn't practical in my case.

So. What to use for backing up sda2 on a schedule, say once or twice a week?

---

### Post by TheFu on 2015-06-15
There are different types of backups, each has a different purpose.

A full disk or partition image requires the disk/partition to be offline to ensure data doesn't change when the backup is taking place.  That is what clonezilla, partimage, dd, ddrescue and other tools like that do.  Generally, we have to boot off different media to make that happen. Not good for a system where zero downtime or automatic backups are needed.

rsync is great for backups with large files that don't change - think media - videos, music, stuff like that.  Things you can't afford to store multiple copies if 1 bit is modified.  rsync is good for making 1 mirror, but IMHO that is not sufficient protection against file corruption or hostile attacks. For that, we need versioned backups from many different points in time, hopefully weeks and months prior to an attack.

That leaves backup solutions that allow versioning. There are some tools which do this well and there are many tools that do not.  On paper, duplicity looks like a great tool, but I've never gotten it working correctly. Tools like dejaDup, duplicati, and a few others are GUIs running with the same underlying libraries as duplicity.  For versioned backups I prefer rdiff-backup. It isn't perfect and there can be issues.

There are also techniques using LVM snapshots for creating backups. If you have ZFS, there ways to send snapshots to remote systems as a backup too.

Not all backup tools support backing up metadata like owners, groups, permissions, ACLs. For media files, that isn't usually important for a home backup system, but inside a business, the changes over time of permissions could be absolutely critical.

I think all of these tools have an "exclude" list.  So you can exclude files seen twice due to bind mounts.

So - having an image backup every 6-12 months is probably fine, then having incremental backups of system files, settings, DBs, list of installed packages and personal data might be sufficient.

I use a mix of methods for backups based on the data. Media uses rsync and only 1 extra copy is made. Documents, settings, DBs, and metadata about the system sufficient to recreate it are fully versioned using rdiff-backup. Most systems have 60 days, but some high-risk systems get 120 days of versioned backups. It is purely a risk mitigation consideration to me.  We do daily backups. Most only require 2-3 minutes for each system to complete. When backups are that fast, it isn't a consideration to NOT do them daily.

---

### Post by Iznougoud on 2015-06-15
Thanks for the feedback. I'll look into the workings of rdiff.

---

### Post by TheFu on 2015-06-15
> **Iznougoud said:**
> Thanks for the feedback. I'll look into the workings of rdiff.

rdiff != rdiff-backup.
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best intro I know.

---

### Post by CharlesA on 2015-06-15
> **TheFu said:**
> rdiff != rdiff-backup.
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best intro I know.

I have that page bookmarked at home (I think at least).

I've been using rdiff-backup for a while now. It's quite handy and seems to be easier to deal with than the way I was using rsync with hardlinks.

---

### Post by TheFu on 2015-06-15
> **CharlesA said:**
> I have that page bookmarked at home (I think at least).

I've been using rdiff-backup for a while now. It's quite handy and seems to be easier to deal with than the way I was using rsync with hardlinks.

My next step into better, easier, faster, backups are LVM/ZFS snapshots.  Saw a presentation at Southeast Linux Fest over the weekend about Sanoid [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid) that really got me thinking.

---

