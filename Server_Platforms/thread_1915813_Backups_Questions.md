---
title: "Backups Questions"
date: 2012-01-27
forum: Server Platforms
---

### Post by needhelppeeps on 2012-01-27
Looking for some answers to help me create a backup solution. I did the obligatory search, but found most answers were overly simplistic. I'd like to make an informed decision, but don't have enough knowledge to do so.


1) First and most important is making sure I never need an emergency restore. To RAID or not to RAID? I had always heard hardware RAID is the best method. However, I've also read online of problems when exact replacement parts are not available. What if I cannot find an exact replacement drive or RAID card, then I'd be sol?

2) Data Integrity: Do simple transfer methods like rsync verify the source and destination match after the transfer is complete and how would I protect against integrity over time with such a setup? Do you guys use some kind of automated change detection system like Aide to see if changes happen on the archived files? How would I know if my archival media has lost integrity?

3) To encrypt or not encrypt:  Encryption seems like a nice feature. It would be nice to know some jerk is not looking at my gfs bikini pics lol but I wonder if that's really worth the risk of losing everything if for some reason I cannot remember the key's password or lose the key entirely.

4) Storing files individually or in archives. Do archives help defend against loss in integrity of individual files or just make it more likely that the whole thing will be corrupt and I won't even be able to access the 99% of the files that would be OK?

5) There does not seem to really be one tried and true way as in the Windows world where Backup Exec seems to be the favored solution. That's a no brainer as thousands of companies use it and there is no shortage of people with advanced restore experience. With "free" solutions, I worry what will happen if I have a corrupt archive or have difficulty restoring? In other words, I don't want to use something that's not been proven time and time again and I don't want to use some software that will unsupported and out of development in a year either (as unfortunately happens sometimes).

Last but not least, media concerns. The "portable" drives commonly used as backup media. I wonder if those use good hardware or if one is better off purchasing a drive cage and buying hard disks separately? Tape drives seem expensive. It seems that I could buy a lot of hard disks for the cost of a tape drive alone.

---

### Post by rubylaser on 2012-01-27
> **needhelppeeps said:**
> Looking for some answers to help me create a backup solution. I did the obligatory search, but found most answers were overly simplistic. I'd like to make an informed decision, but don't have enough knowledge to do so.


1) First and most important is making sure I never need an emergency restore. To RAID or not to RAID? I had always heard hardware RAID is the best method. However, I've also read online of problems when exact replacement parts are not available. What if I cannot find an exact replacement drive or RAID card, then I'd be sol?

2) Data Integrity: Do simple transfer methods like rsync verify the source and destination match after the transfer is complete and how would I protect against integrity over time with such a setup? Do you guys use some kind of automated change detection system like Aide to see if changes happen on the archived files? How would I know if my archival media has lost integrity?

3) To encrypt or not encrypt:  Encryption seems like a nice feature. It would be nice to know some jerk is not looking at my gfs bikini pics lol but I wonder if that's really worth the risk of losing everything if for some reason I cannot remember the key's password or lose the key entirely.

4) Storing files individually or in archives. Do archives help defend against loss in integrity of individual files or just make it more likely that the whole thing will be corrupt and I won't even be able to access the 99% of the files that would be OK?

5) There does not seem to really be one tried and true way as in the Windows world where Backup Exec seems to be the favored solution. That's a no brainer as thousands of companies use it and there is no shortage of people with advanced restore experience. With "free" solutions, I worry what will happen if I have a corrupt archive or have difficulty restoring? In other words, I don't want to use something that's not been proven time and time again and I don't want to use some software that will unsupported and out of development in a year either (as unfortunately happens sometimes).

Last but not least, media concerns. The "portable" drives commonly used as backup media. I wonder if those use good hardware or if one is better off purchasing a drive cage and buying hard disks separately? Tape drives seem expensive. It seems that I could buy a lot of hard disks for the cost of a tape drive alone.

1. For a home server where throughput isn't the most important factor, I would encourage you to use software RAID (mdadm).  It's very proven, is portable to any linux host, and is not hardware dependent. Also, it's free :)

2. Rsync does verify that the source and destination are exactly the same.  You could use a rsync command like [this]("http://www.techrepublic.com/blog/security/use-rsync-for-filesystem-integrity-auditing/279") to audit your filesystem integrity.  For my media storage (pictures, home movies, music, etc.), I like to make a text file that I has MD5 sums of all of my files in that directory.  That way I can easily run a diff on the new MD5 vs the old with a Bash script and quickly see if something has changed, and which version is correct.

3. In a home setting, I would encourage you not to encrypt.  If someone has physical access to your computer to steal it, you have far bigger problems to deal with.  Also, it's one more layer to troubleshoot and have potentially go awry.

4. I'd store files individually (meaning not in archives).  It would make an MD5 sum test easier to single out a few bad files and you'd potentially only lose or have to restore a smaller portion.

5. A few rsync scripts or rsnapshot are dead simple had very proven.  There is no archive to corrupt, because you're creating a one-to-one backup (unless you want to create versions with hard links, but that's another story :) )

6. Just use hard disks, they're much cheaper for a home backup solution.  Things like family photos and videos, I also burn to dual layer DVD's each quarter, and backup offsite to my colocated fileserver too just for an extra layer of protection.

---

### Post by drmrgd on 2012-01-27
I totally agree with rubylaser about using something like rsnapshot.  Actually, I just installed it and was playing around with it yesterday, and I love it!  It's extrememly simple to set up, and so far seems to work great.  I was just using rsync and manually managing my backups.  This took all the work out of it and automated it for me.  I'd recommend checking it out.

---

### Post by needhelppeeps on 2012-01-27
Just wanted to come back and say great answers. I believe I now have enough information to begin experimenting with the exact scripting I need once I have the new backup machine ready.

---

### Post by TheFu on 2012-01-28
Excellent questions. Your concerns are in the right places.  Compared to what MS-Windows requires, backups on Linux/UNIX systems are simple. Data consistency is key - that usually isn't an issue except for DBMS data files, like an open MySQL DB.  Most people get around that by dumping the DBMS to a text file just prior to doing a backup, then they backup both the text-dump AND the actively open SQL DB files.  Most other files do not have this issue, since they will be closed or saved in a known state - safe to backup.  To get a fully consistent backup, you want to be in single user mode, but that isn't usually viable for a server.

RAID - in a low budget environment where you can't either have a spare HW RAID controller onsite or fly one in in a few hours regardless of cost, then you need to stay with software RAID.  RAID is not a backup, which you already realize.

Data integrity is an issue for all storage devices - all the time. The solution to that is having incremental backups - multiple sets that go back long enough that you'll notice the corruption before the last "good" backup has been overwritten.  The only file system that I know which includes data integrity validation is ZFS.  ZFS isn't really an option on Linux due to FUSE performance.  If you are really concerned about validation of files, I can only suggest using PAR2, but having a par2 parity set built on previously corrupted files doesn't really help.  I've only seen corruption on failing physical disks or on directories that hadn't been  re-written in over 4 years. Those failures have been recognized pretty quickly - within a few days at most.  Lazy bits are a real concern over time.  I had a lazy-bits issue last week on a backup disk. The primary disk hasn't shown any issues - both were purchased on the same date.

File system encryption - my rules here are simple.  I encrypt any backups that leave the location OR could leave the location.  Portable drives are good for this. Laptops are encrypted. If you worry about corruption, have two or more physical backup disks that you swap.  Backup the encryption keys in multiple, secure locations.  I keep mine inside a password manager along with lots of other really important data and passwords.

Storing files or archives - well, if you use a real backup system, then your files will be organized in some way. Rsync alone is not a good backup solution for files that change over time. It is fine for media collections and photographs.

Here is a best practices article: [http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups) for backups.

Some software options for Linux backups. The rsnapshot scripts have been proven, but they lack some of the other "best practice" goals for a backup solution.  If you are doing a single Linux box, you want to keep it simple. 
* Duplicity / Duplicati
* rdiff-backup
* Back-in-time - really simple and easy to understand
* rbackup / rsnapshot
* Bacula - enterprise like
* Amanda - enterprise like

are a few tools to consider.  Personally, I've been using rdiff-backup for about 4 years across about 20 different servers.  I've had to restore a few times too. They were successful.  rdiff-backup has a very similar command line as rsync, but offers so much more capability over a simple rsync.

You don't need to wait for a backup server to start performing backups. Your data is too important to risk that - get a stupid USB drive and start backing up this weekend.

Get the most critical data off-site. Tornados, floods, fires happen everywhere.

Hopefully some others will bring their favorite backup solutions to your attention too.

---

