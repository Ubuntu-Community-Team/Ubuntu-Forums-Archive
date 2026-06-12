---
title: "optomise a disc for large files"
date: 2010-06-08
forum: Server Platforms
---

### Post by chrisbay90 on 2010-06-08
Hey guys,  Im adding a new drive to a linux box, this disc will almost exclusivly be an NFS for backups.  Is there a way to format it to be optomised to store a small number of large files?  something to do with the block size or number of inodes?

---

### Post by BobVila on 2010-06-08
I'm covering my head to shield from the file system wars I'm sure I'll start with this response, but you'll see the most benefit by formatting it xfs instead of ext4, which is the default on newer ubuntu boxen.

---

### Post by chrisbay90 on 2010-06-09
Thanks for the sugestion Bob :)!
Being that it will be used to backup important data I am cocerned about its reliability*. Now i know the linux community is full of passionate divisions over these sorts of things, however in general terms is xfs known to be less reliable than ext4?

Also Bob or anyone else out there, when partitioning up a disc how do i specify block sizes and do you have any recomendations of what size is should use. 2tb drive, will hold 5-10 files in the region of 100gb and 50 files in the range of 1-10gb and perhaps a few bits of miscellany as well.

*Being that is is only going to contain the backups im not overly concerned about data integrity as for there to be any real data loss both the original and the backup data must be lost in a windows small enough not to be noticed and rectified.

---

### Post by disabledaccount on 2010-06-09
Greatest differences in performance of filesystems can be seen mainly with small and medium-size files/records during high I/O load with mmap, re-read or re-write oparations, particulary when comparing distributed/array-based or high-level filesystems. In your case, tunning block size, stride etc. is of little sense - you wont see any difference.
Filesystems are protected with redundacy - on single disk your backups are not safe - regardless of what FS you will use.

---

