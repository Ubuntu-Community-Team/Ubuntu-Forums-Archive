---
title: "Backup VM's"
date: 2010-04-20
forum: Server Platforms
---

### Post by erdanblo on 2010-04-20
Hi,

I'm thinking to use rdiff-backup for backup my VM's. I tried to a test with a virtualbox image, and in the second exec of rdiff, it copied all file again (not incremental).

I executed this way:

rdiff-backup --terminal-verbosity 9 src/ dest/

are there any error?

are there something to down needed traffic? My problem is i need to backup in a remote server, and i have a 320kbits/s connection. I can't upload 20/30GB all days, when the change in VM's are 1Gb Max.


I thinked that rdiff-backup take incremental backup of the blocks modified.

My target is get to backup my VM's which is at Logical Volumes (LVM). Get snapshot of that LVM's, use dd, compress with bzip2 or similar, and up to my remote host using rdiff-backup.


my log: [http://pastebin.com/DT7F1Knp](http://pastebin.com/DT7F1Knp)
ls of source directory: 

dani@dani-desktop:~/Desktop/backup$ > ls -l origen/
total 4823168
-rw------- 1 dani dani 4938916352 2010-04-20 10:00 HaserfrochPX - test.vdi

---

