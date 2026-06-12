---
title: "Strangely Corrupted MP3 files"
date: 2024-05-13
forum: The Cafe
---

### Post by nicolasdentremont on 2024-05-13
This is more of a remark about something strange that has happened to my MP3 collection rather than a help request.

I had a collection of MP3s stored on an external HDD. The HDD started making weird noises so I figured that it would die soon. I copied what I could off of it, it took a very long time as the file transfer would repeatedly drop to 0 for a minute or two every few files. When it finished, all the files looked like they were accounted for and the file sizes were correct.

Upon playing my music collection, I have discovered that now some of my tracks have bits and pieces of other songs mixed into them. Mostly at the beginning of the track, some of them will switch back and fourth from song to song several times before it starts to play properly.

I managed to get some of my movie/show collection off the same drive. The video files don't exhibit the same condition.

I honestly thought that was kinda funny and was wondering if this has happened to anyone here before?

---

### Post by TheFu on 2024-05-14
File corruption can happen for thousands of reasons.  It has always been possible since HDDs were first created in the 1960s.

The only file system that validates what the computer sent to the disk is actually what was written is ZFS.  All the others trust that the information send was written.
Over time, files that aren't re-written can become corrupted by "bit rot".  There are magnetic fields which create the 0s and 1s used to convey information. If they aren't access and refreshed before the magnetic field dips below the ability of the drive to "feel" the magnetic state of the data, then that data is lost.

The most common example of this in the world over the last 30 yrs has been the MS-Windows boot areas.  Those are seldom updated once installed, so as a computer ages and they are seldom referenced, the drive hardware doesn't get a chance to notice the bit-rot and refresh the magnetic levels.

There are lots of solutions for this.  The easiest is to perform periodic backups of the system. As the files are viewed by backup software, the drive hardware reads each byte and if any are showing less magnetism, the drive will automatically refresh the data.  Of course, copying the files to another different location is another way, since doing that forced all the data to be read again.   Doing almost anything that prevents the data from just sitting, not being referenced, for more than a year, should be sufficient to keep the magnetic levels sufficient to prevent bit rot.

Beware that some tools won't actually look at all the bytes of data when deciding if a file is new or not. It may only look at the modification time and decide NOT to look any farther.  Also, know that moving a file within the same file system doesn't actually copy any data. It just moves the pointer between where the file data is stored and which directory it is in.  This is why moving any file, regardless of size, within the same file system is nearly instant.  

So, once a year, just copy entire disks (source) to a spare disk that gets wiped when full. Don't call it a backup. Your backups need to be on specific disks.  Copying 4TB should take about 24 hours.  For most people, that is sufficient.

Or you can use ZFS and run a scrub to validate the data.  That reminds me. I need to setup a monthly ZFS scribe on my play ZFS system.  I need to learn more about ZFS. There's almost more to learn and that time competes with our other goals/tasks in life. [https://openzfs.github.io/openzfs-docs/man/master/8/zpool-scrub.8.html](https://openzfs.github.io/openzfs-docs/man/master/8/zpool-scrub.8.html)

I just scubbed 2 zpools.
```
$ sudo zpool status -v bpool
  pool: bpool
 state: ONLINE
  scan: [B]scrub repaired 0B in 00:00:00 with 0 errors on Tue May 14 09:26:04 2024
[/B]config:

        NAME                                    STATE     READ WRITE CKSUM
        bpool                                   ONLINE       0     0     0
          8fcc521e-fd06-104c-9bd3-eed4af5b09e4  ONLINE       0     0     0

errors: No known data errors

$ sudo zpool status -v rpool
  pool: rpool
 state: ONLINE
  scan: **scrub repaired 0B in 00:00:18 with 0 errors on Tue May 14 09:26:26 2024**
config:

        NAME                                    STATE     READ WRITE CKSUM
        rpool                                   ONLINE       0     0     0
          5a99e6df-b48b-db41-9dde-acf1247c092d  ONLINE       0     0     0

errors: No known data errors
```
So, no errors were found. That's good news.  That install is about 11 months old and on an NVMe drive, so I wouldn't expect any bit-rot yet.

I do have 10+ yr old HDDs in use.  I wouldn't be surprised if they had some bit rot.  

There are other methods to ensure data integrity.  Using par2 files is a way that people have transferred huge files over the internet for 20+ yrs with integrity checking and some ability to correct errors built-in.  For my most important data, I have 10% par2 files stored with the data.  When I was archiving things to CDROM and DVD storage, I used 10% par2 files as a way to ensure I was at least aware of corrupted files and might be able to correct issues, if the corruption was less than 10%.  I've had to use that a few times over the decades.  For data that I only need a yes/no answer - corrupted or not - using 1% par2 files seems sufficient.

This does point out that I really need to transition my data storage from ext4 to zfs.  Even if I don't change the OS from ext4, using ZFS for data areas to ensure corruption is minimized over time makes sense.   One more thing to do.  Sigh.

---

### Post by nicolasdentremont on 2024-05-15
I have seen ZFS referenced a few times in discussions around here but I haven't got to the point where I want to experiment with different file systems yet.

I just thought it was funny that a failing HDD could splice songs together and have the resultant file still be playable.

---

### Post by TheFu on 2024-05-16
If a critical part of the file isn't corrupted, most programs will continue until they cannot.  This is very common for media files, since they are often streamed and streaming has hiccups.

For other programs, corrupted data is a common way to break out of a program and attack the operating system.  For programs being run as an end user, this usually doesn't allow much access, but if a program is being run with elevated privilege, which noobs do far too much (sudo), then they may give full access to the OS.

Data corruption needs to be prevented.

---

