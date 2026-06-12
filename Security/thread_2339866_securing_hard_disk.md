---
title: "securing hard disk"
date: 2016-10-13
forum: Security
---

### Post by ltoso on 2016-10-13
Hi, I want to make sure if somebody takes out the internal hard disk of my computer running Ubuntu,
 he should not be able to access my files without knowing access password even if he has installed the hard-disk to his 
Computer to access it, and I should be able to
Rsync the files on the hard disk to another hard disk through a cron, for 
Keeping my files backed up, so now both the hard disks will be encrypted.
One will have the latest version of files other will have version of files little 
Older, as I intend to run rsync every 6 hours

Please recommend

---

### Post by ian-weisser on 2016-10-13
Not sure I understand your question.
You already know to use encryption, and want to use rsync.
What more are you looking for?

---

### Post by ltoso on 2016-10-14
Thanx for replying, I know it has to be encrypted but don't know how to encrypt all the hard disc with a password and I also want to rsync all the contents from one encrypted hard disk to another on regale basis to keep data safe from hard ware failure. Encrypt it to save data from physical theft of hard disk.

---

### Post by ian-weisser on 2016-10-14
Full-disk encryption requires LVM, which requires re-partitioning the disk.
The easiest way to do this is by reinstalling. The Ubuntu installer will re-partition for LVM, install LVM, and install encryption.

Re-partitioning will destroy all data on your disk. Save to external media before installing.

Encryption has it's own minor hassles and requirements, just like all new technologies.

---

