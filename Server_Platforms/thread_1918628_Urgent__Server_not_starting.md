---
title: "Urgent : Server not starting"
date: 2012-02-01
forum: Server Platforms
---

### Post by murataht on 2012-02-01
first, i saw a messge from syslog: "ext4 directory index full"; then I tried to start the server, it stuck each time with a message "udevtrigger terminated ..."; recovery mode stucks there, too. I am using a live cd 11.4 to fix the problem ...

The server is on ubuntu 10.4 64 version; 

I looked into the fstab, the uuid is correct.

currently I am running "e2fsck -vfD" to correct the directory full problem; but it is taking very long time. even with the verbose mode there is no extra information on the screen. 

Does anyone have any idea. Thanks in advance.

---

### Post by TheFu on 2012-02-01
This is a shot in the dark.  There are 2 ways that a file system can be filled, one is what we all know - out of disk space.  The other happens much less often, but can still happen, **out of inodes**.

* df -k
* df -i

These will tell you if the file systems are full and how full they are.

The last time this happened to me, I was writing backups to the / partition by accident. The partition for backups did not get mounted, so backups were written to the file system that held the mount point directory.

---

### Post by ian dobson on 2012-02-01
Hi,

Do you know which file system is causing the problem (/boot or /root), and is the disk file format actually ext4 (and not ext3 that the ext4 file system drivers are loading).

I would recommened you try mounting the file system from a live CD, checking it with e2fsck and try and find what directory is filling your inodes. Mail servers that are not using the mbox file format are known to create huge numbers of files in directories.

Regards
Ian Dobson

---

