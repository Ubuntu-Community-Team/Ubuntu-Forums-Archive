---
title: "BackupPC - Rsyncd compression problem"
date: 2008-03-29
forum: Server Platforms
---

### Post by dlcobb on 2008-03-29
I had success with Backuppc and Rsyncd in backing up a number of XP clients.

Then, after several month, I started getting two errors when backing up one client. Either "Got fatal error during xfer (Child exited prematurely)" or the server locked up totally requiring a reboot.

After experimentation, I found that turning off compression seems to resolve the problem.

I assume that there is one or more files that the compression chokes on.  

How can I discover which files cause the problem?  I want to compress if possible.

---

### Post by dlcobb on 2008-05-17
> **dlcobb said:**
> I had success with Backuppc and Rsyncd in backing up a number of XP clients.

Then, after several month, I started getting two errors when backing up one client. Either "Got fatal error during xfer (Child exited prematurely)" or the server locked up totally requiring a reboot.

After experimentation, I found that turning off compression seems to resolve the problem.

I assume that there is one or more files that the compression chokes on.  

How can I discover which files cause the problem?  I want to compress if possible.

It runs out that compression was not the problem after all.  After a while, even with compression off, the errors occurred.  The real culprit was a intermittent memory error that only caused problems when backing up a unit with a large amount of data.

---

