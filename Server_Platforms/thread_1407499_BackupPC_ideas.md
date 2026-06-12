---
title: "BackupPC ideas"
date: 2010-02-15
forum: Server Platforms
---

### Post by TheGameAh on 2010-02-15
Hey guys.

I've been tasked with putting together a backup system for some Cad files.  They wanted a 6 month history.  As in, they can retrieve a version of any file on their share for 6 months.  Not a problem for BackupPC.

But of course, people want to change things.

I explain the system to them, give a quick demo, and then they ask, "Well is it possible to maintain a permanent history?  As in forever?"

So we've gone from 6 months to forever.  Nice.

Anyway, racking my brain trying to come up with something.  Write to removable media every so often?  Use hot swap drives?  When one starts to fill up, just slap in another?  Would this work?

Anyone ever have something like this scenario?

---

### Post by hessiess on 2010-02-15
Use a version control system, i.e. GIT, SVN etc.

VCS's manage disk space by only storing the deltas(difference) between two files, so use a LOT less disk space. My SVN repositoy containing several hundred .blend files and a few thousand images which I started about a year ago is only about a hundred gigabytes, Without delta compression this would be two or three times as large. Anyway, terrabyte drives are dirt cheep these days, set up a RAID5 array and add disks as needed ;).

---

### Post by TheGameAh on 2010-02-16
Hmm interesting, never played with any of that.  Do you have any software you recommend?  Open source hopefully?

If a file is deleted, is it possible to retrieve the file?  This doesn't sound exactly like a backup system, but might do the trick.

---

### Post by japsai on 2010-02-16
Yes, deleted files can be retrieved.

The amount of compression depends very much on the underlying data-type of the files.

---

### Post by hessiess on 2010-02-16
> **TheGameAh said:**
> Hmm interesting, never played with any of that.  Do you have any software you recommend?  Open source hopefully?

If a file is deleted, is it possible to retrieve the file?  This doesn't sound exactly like a backup system, but might do the trick.

A version control system on its own is not the same as a back up system, the data repository and working copy can be stored on the same computer. However they also make it trivial to synchronise the data across n number of computers. Edits can be preformed concurrently on the same file, by multiple people and the VCS will do its best to merge the changes automatically. Meaning that they can also be used for backup. For example you could have a backup server which periodically pulls down a local copy of the repository from the main server using a cron job.

Personally I use Subversion (SVN), however one of the distributed version control systems would probably fit your needs better. GIT is a popular one, but it does not run well on Windows from what I have read about it. Bazaar is another one which is written in Python, and should run on any platform where Python is available, including Windows.

---

