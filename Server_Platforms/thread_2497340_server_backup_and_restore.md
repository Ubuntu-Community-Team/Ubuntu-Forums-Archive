---
title: "server backup and restore"
date: 2024-05-01
forum: Server Platforms
---

### Post by m1s3rys1gn4l on 2024-05-01
dear team and community,
i am early stage noob at ubuntu server,

let me explain what exactly i want,
i have setup a server in my office, i would like to play with it,
now my question is if i messed up with anything is there any way to make it fresh as it was installed.
cause i know i will destroy it somehow :( 

i have used some vps service and there was a option for reinstalling OS that was awesome.

---

### Post by TheFu on 2024-05-01
Make backups.  Usually we do versioned backups and retain at least 6 months for low-risk servers and a year of backups for high-risk, internet-facing servers.

Test the restore to be certain you got it all.

There's no 1-click backup for servers. Sorry.

There are trade offs.  The fewer steps involved, the longer and more storage will be needed.  For slightly more complexity, extremely efficient, storage efficient, fast, versioned backups that need just a few steps to restore are possible, but these are usually not for noobs.  Internal knowledge of how Linux actually works is required, but the results are impressive.  For example, here's the backups for an email gateway server:
```
# rdiff-backup --list-increment-sizes spam2
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed May  1 00:03:24 2024         3.89 MB           3.89 MB   (current mirror)
Tue Apr 30 00:03:25 2024         1.33 KB           3.90 MB
Mon Apr 29 00:03:30 2024         1.32 KB           3.90 MB
Sun Apr 28 00:03:28 2024         1.27 KB           3.90 MB
Sat Apr 27 00:03:30 2024         4.87 KB           3.90 MB
...
Fri May  5 00:03:17 2023         1.30 KB           4.42 MB
Thu May  4 00:03:24 2023         1.63 KB           4.42 MB
Wed May  3 00:03:17 2023         1.61 KB           4.42 MB
Tue May  2 00:03:16 2023         1.25 KB           4.43 MB
```

That backup has everything needed to restore to a specific point in the last year.  Because it is a gateway, it doesn't actually have an data.
Last night, the backup took, let's see ...
```
=== Time for Backups to spam2 === 
StartTime 1711944209.00 (Mon Apr  1 00:03:29 2024)
EndTime 1711944212.63 (Mon Apr  1 00:03:32 2024)
ElapsedTime 3.63 (3.63 seconds)
TotalDestinationSizeChange 1276 (1.25 KB)
```
3.63 seconds.  Very efficient.

Of course, systems with more data take longer and use more storage, but most servers here need less than 1 minute to perform the backup.  
For a system with 20TB of of data ...
```
# rdiff-backup --list-increment-sizes istar/
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed May  1 04:35:07 2024         19.1 GB           19.1 GB   (current mirror)
Tue Apr 30 04:35:07 2024         56.4 MB           19.1 GB
Mon Apr 29 04:35:07 2024         52.3 MB           19.2 GB
...
Sat Feb  3 04:35:08 2024         74.7 MB           26.5 GB
Fri Feb  2 04:35:08 2024          152 MB           26.6 GB
Thu Feb  1 04:35:08 2024         61.0 MB           26.7 GB
```
Most of that data isn't part of the system backups.
```
StartTime 1714552507.00 (Wed May  1 04:35:07 2024)
EndTime 1714552624.71 (Wed May  1 04:37:04 2024)
ElapsedTime 117.71 (1 minute 57.71 seconds)
TotalDestinationSizeChange 61543270 (58.7 MB)
```
So, about 2 minutes.

I've posted scripts and important "how to restore" using the same method in these forums.

If your server was installed with a volume manager like LVM or ZFS, then snapshots can be used as part of a great backup solution.  ZFS supports sending snapshots to a remote server using zsend, for example. There are ZFS specific backup scripts/tools for this to make life easier.

Again, there are trade-offs for all backup methods.  The trick is to know what you need in the end (a good restore) and work backwards so nothing is missed without grabbing too much useless stuff.

---

