---
title: "Fileserver down. ls -la stalls the computer"
date: 2011-04-08
forum: Server Platforms
---

### Post by ramvi on 2011-04-08
I have a file server that suddenly stopped working. Files suddenly won't list. ls works but it just stalls on ls -la. We have two disks in raid 1 and another backup which is the files mv-ed there. fsck reports problems on both the raid disks and I guess this must be the reason. But ls -la hangs on the backup disk as well, which is weird as the sector/inode errors shouldn't be moved over with mv. What can it be? Please help me troubleshoot.

The computer isn't brought to a full stop. I can change ttys and continue but I'm unable to stop the ls -la process.

Some files are owned by numbers ie 11388 instead of a username like root.

Edit: ls -la works as expected in each of these dirs /sdc1/snapshopts/daily.0/knutgeir/
but as I get to home: ../knutgeir/home/ it stalls. Home got 215 files/folders. If I continue into ramvi: ../knutgeir/home/jon , which only got like 7 files/foldes, lf -la still stalls

Why?

---

