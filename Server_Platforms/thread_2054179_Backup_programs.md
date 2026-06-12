---
title: "Backup programs?"
date: 2012-09-06
forum: Server Platforms
---

### Post by dglad4 on 2012-09-06
Hi all, I need some help finding a suitable application to run backups with. I'm using Ubuntu Server 10.04 LTS x64 as the operating system on my 8TB NAS (soon to be 12.04 at the end of the year). The machine runs beautifully serving all sorts of clients via SSHF and Samba. I have 16TB worth of drives (2x1TB/4x2TB/2x3TB) and as you can tell every primary running drive has a backup drive. Data stored doesn't change a whole lot and isn't highly important but if a drive were to die I'd just like to replace the primary with the backup and buy another drive to become the new backup.

Essentially I need a program that can clone all data sort of like a sync, removing deleted/moved files on the backup drive when changed on the primary and dealing with 1 file at a time (so if the primary were to give in whilst running a backup, files yet to be replaced will remain on the backup drive).

My current backup plan works but has a huge vulnerability. I delete all data on the backup drive and fresh copy all data from the primary. So if the primary were to die I'd have lost all non-duplicated data. Also, it takes longer due to copying all data rather than what is needed.

So to recap, I need a program that can:
- Copy data from one drive to another
- Skip already existing duplicate data
- Replace updated/changed files
- Delete moved/deleted data (otherwise the backup drive will run out of space)

Thanks heaps. If you need more info just ask.

Thanks,

dglad4.

---

### Post by LHammonds on 2012-09-07
Well, if you really want each drive to backup / mirror another drive, you could configure the drives in RAID 1 (mirroring) which will do what you are looking to accomplish.

However, if you are past the point of configuring the server, your next best bet would be to use rsync.  Schedule an rsync job to run multiple times throughout the day and have it "sync" your data files to your backup drive.

However, I wouldn't stop with just rsync.  That just gives you a duplicated set of files that stay in sync with the original drive.  If you delete a file by accident and the sync job runs, it will remove your backup copy too!

You might also want to compress your data files into a single archive to retain full backups periodically so you can retrieve old files.

As for your operating system, I hope you setup everything using LVM because you can set aside some free, unallocated space in the LVM and use snapshots to capture your OS while it is online and archive it using fsarchiver...then remove the snapshot.

Take a look in my sig for examples of how I accomplished this on my basic Ubuntu Server setup.

LHammonds

---

### Post by sandyd on 2012-09-07
I would look towards rdiff-backup

Rdiff-backup does incremental backups, so if you screw something up, you still have restore points you can fall back on.

---

### Post by dglad4 on 2012-09-09
Thanks guys, I've finally got rsync working how I need it to. I've never had it running properly previously and I have found out why. I've had the -c or checksum turned on without realising how CPU intensive and slow the option is. Time comparisons are all I need, as there is no sync happening (where the backup files are edited). In theory, as the backup drives are used only on the same machine as the primary drives the files on the backup will always be older, therefore edited files on the primary will have newer dates than the backups causing the backup to be updated. No checksum needed, less CPU intensive, backup runs at last.

These backups will be run weekly, with high importance folders utilising another backup daily to remote computers.

Thanks again,

dglad4.

---

