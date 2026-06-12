---
title: "rdiff-backup freezing?"
date: 2024-02-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2024-02-19
I have three machines running ubuntu mate 22.04 that use rdiff-backup.  For some reason, on all three machines, rdiff-backup randomly freezes during its run process.  On one machine I thought it was the file it was freezing at so I removed that file from the source but it made no difference.  All three machines have been backing up with no problem for a few years.  Has anybody else experienced any problems with their rdiff-backup?  (I'm wondering if it some 22.04 update).

---

### Post by Quarkrad on 2024-02-19
Doh...  schoolboy mistake (although I'm a little old to be a schoolboy).  Two of the three machines causing me trouble were machines that do have lvm running.  I created a vm on the two trouble machines, for different but specific reasons, and the .qcow2 file was in a home folder being backed up. Rdiff-backup was probably OK but taking a long time to copy the large file.  Once I removed the folder from the backup list (I use a *include* list as part of the rdiff-backup script) the backup ran at its normal speed.

---

### Post by Quarkrad on 2024-02-19
Can't marked thread as solved - not in thread tools options.

---

