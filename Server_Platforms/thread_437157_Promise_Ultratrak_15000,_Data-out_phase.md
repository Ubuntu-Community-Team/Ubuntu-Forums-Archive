---
title: "Promise Ultratrak 15000, Data-out phase"
date: 2007-05-08
forum: Server Platforms
---

### Post by mbradlcu on 2007-05-08
for me and the 6 other folks who use this device, I have a fix for the following issue, If anyone has a more proper fix please let me know!

here's the errors (note this was the same for ext3 and ext2):

[ 850.050388] (scsi0:A:0:0): parity error detected in Data-out phase. SEQADDR(0x85) SCSIRATE(0xc2)
[ 850.050400] No terminal CRC packet recevied

[ 850.082564] REISERFS: abort (device sda1): Journal write error in flush_commit_list
[ 850.082573] REISERFS: Aborting journal for filesystem on sda1

the fix seems to be changing the block size:
mkfs.ext3 -b 1024 /dev/sda1

history:
I upgraded the firmware on the Ultratrak but it didn't fix the issue. 
I had a 2.2 raid5 array setup on the Ultratrak and formatted it with the default mkfs.ext3 /dev/sda1,
Files would copy over for a couple seconds then I would get warnings that `cp` couldn't copy to a "read only file system"  

thanks
Matt

---

