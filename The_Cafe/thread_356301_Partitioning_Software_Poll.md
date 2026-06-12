---
title: "Partitioning Software Poll"
date: 2007-02-08
forum: The Cafe
---

### Post by louieb on 2007-02-08
I don't have any problem backing up and restoring a PC before changing disk partitions. Tar works well for backup and restore of Linux . But restoring XP is such a bitch.
The XP backup software needs a floppy drive in order to restore from a full backup. How many of the newer PCs have one? I have trashed more that one XP install while shrinking the windows partition using GParted.  So I am thinking of getting a commercial product to resize windows (NTFS) formatted partitions. Just wondering what you all have used and was it trouble free and easy to use.

---

### Post by renzokuken on 2007-02-08
one question, did you defrag the ntfs partition before you shrank it. i think you should always do the defrag first on ntfs, especially on an old drive or one that is over half full

---

### Post by igknighted on 2007-02-08
> **louieb said:**
> I don't have any problem backing up and restoring a PC before changing disk partitions. Tar works well for backup and restore of Linux . But restoring XP is such a bitch.
The XP backup software needs a floppy drive in order to restore from a full backup. How many of the newer PCs have one? I have trashed more that one XP install while shrinking the windows partition using GParted.  So I am thinking of getting a commercial product to resize windows (NTFS) formatted partitions. Just wondering what you all have used and was it trouble free and easy to use.

Actually, if you run disk-check and defrag your drive several times GParted is about as good as it gets.  Partition Magic is the big-name commercial software you hear about, but it has more issues. especially with linux.  I suppose one could resize Windows with Partition Magic (hey, if it screws up you have somewhere to send your angry emails to at least :-P), and then create your linux partition with GParted, but I would just use GParted if it were my hard drive.

---

### Post by Eddie Wilson on 2007-02-08
When I deal with a Windows partition I usually use PartitionMagic.
Eddie

---

