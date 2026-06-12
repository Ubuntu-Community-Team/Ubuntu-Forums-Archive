---
title: "unable to read inode"
date: 2009-07-06
forum: Server Platforms
---

### Post by ozPATT on 2009-07-06
Hi, I have setup a server (8.04) on a spare machine I have, it used to work fine, but stopped some time ago. I have just decided to work out why :) 

The main problem I have at the moment, is that it won't complete the boot procedure. It keeps coming up with 

unable to read inode block - inode=612700, block=12255239 init:rc-default main process (2626) terminated with status 127

Does this mean anything to anyone? I can't log in using ssh because it hasn't booted completely, and I can't seem to work out how to get to any command line to check for messages or update any files. 

I have data on the hard drive that I don't want to lose, so I am reluctant to try installing the system again. Any ideas on what could be the problem or how I can fix it? 

Thanks

Patrick

---

### Post by pebo on 2009-07-07
Try booting into a live cd and running e2fsck (assuming you are using ext2 or ext3) on the drive in question. If that doesn't fix any errors then it looks like you have a hard disk failure on your hands and I can't help you there. You still might be able to save data using the live cd though.

---

