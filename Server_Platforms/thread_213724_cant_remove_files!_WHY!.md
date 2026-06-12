---
title: "cant remove files! WHY!??"
date: 2006-07-11
forum: Server Platforms
---

### Post by Simpel on 2006-07-11
Hello!

I admit it, i'm a n00b....but still, this doesn't make any sense. I have some files that I want to remove on a mounted harddrive, and I can't do it, I tried as root, as sudo, with rm -f....and all i get is:

rm: cannot remove `*****THE FILE****': Read-only file system

why goooooood WHYYYYY!!!??

I run the Drapper version..as a server...

---

### Post by aggiechemist on 2006-07-11
I guess the question is why is it read only?

Try looking around the /etc/fstab file, make sure the mount paramaters in there are set so taht it is read and write.

Option 2 would be to make sure it is not an NTFS system. If you are working on a windows NTFS partition, I'm not sure if you're ever allowed to delete files. NTFS file control is still limited.

Good luck.

---

### Post by MetalMusicAddict on 2006-07-11
Without more info I can only guess the drive was mounted read-only. Can you give more info about the drive? Filesystem and whatnot?

---

### Post by lamego on 2006-07-11
Do you know what a file system is ?
The "Read-only file system" makes all sense.
If it is a NTFS file system then it can only be mounted R/O (RW is not supported) that would explain your problem.
Otherwise please type "man mount", is is very helpful for whoever needs to manage a server.

---

### Post by Jasper Houtman on 2006-07-11
> **lamego said:**
> Do you know what a file system is ?
The "Read-only file system" makes all sense.
If it is a NTFS file system then it can only be mounted R/O (RW is not supported) that would explain your problem.
Otherwise please type "man mount", is is very helpful for whoever needs to manage a server.

Actually there is a project for NTFS which allows writing to such volumes. Still very unstable though. Mess up with those and it's bey bey NTFS volume :P

---

### Post by Simpel on 2006-07-11
Wow, those were som fast answers....here's the output from fstab, hopefully it helps;


filesystem mountpoint type options dump pass

/dev/hdb2 /mnt/120gb/ ext3 defaults 0 0

the thing is that all of that seems fine to me, doesn't it??

and o! I should also say that I tried to remount the harddrive but it seems as if the system is running on that drive so I can't just remount it....

and the second Ooo! is that i rebooted the system and did a checked the disk...ubuntu found som disk errors and fixed them....didn't solve this problem though..

---

### Post by Akita on 2006-07-11
Check the output of dmesg for anything that would indicate that the system forced the mount to R/O.

---

### Post by Simpel on 2006-07-11
yea...somethings wrong there....I don't understand any of that though! ...help! :)




EXT3-fs error (device hdb2): ext3_free_branches: Read failure
inode=1933345, block=7133751
[4294881.061000] Aborting journal on device hdb2.
[4294881.063000] EXT3-fs error (device hdb2) in ext3_reserve_inode_write: Jour
l has aborted
[4294881.064000] EXT3-fs error (device hdb2) in ext3_truncate: Journal has abo
ed
[4294881.065000] EXT3-fs error (device hdb2) in ext3_reserve_inode_write: Jour
l has aborted
[4294881.066000] EXT3-fs error (device hdb2) in ext3_orphan_del: Journal has a
rted
[4294881.067000] EXT3-fs error (device hdb2) in ext3_reserve_inode_write: Jour
l has aborted
[4294881.068000] EXT3-fs error (device hdb2) in ext3_delete_inode: Journal has
borted
[4294881.068000] __journal_remove_journal_head: freeing b_committed_data
[4294881.068000] __journal_remove_journal_head: freeing b_committed_data
[4294881.068000] __journal_remove_journal_head: freeing b_committed_data
[4294881.071000] ext3_abort called.
[4294881.071000] EXT3-fs error (device hdb2): ext3_journal_start_sb: Detected
orted journal
[4294881.071000] Remounting filesystem read-only

---

### Post by invisibastard on 2006-07-11
I keep getting the same problem. I run normally for a while, then suddenly everything goes to hell and I get that same error. 

It seemed to have started for me when I installed vmware server. I can't say for sure, though. 

I found this in dmesg:
[17221227.084000] EXT3-fs error (device hdb1): ext3_xattr_delete_inode: inode 3473796: bad block 256
[17221227.088000] Remounting filesystem read-only

I guess I will reboot and run fsck. 

strange. 

thanks,
rich

---

### Post by Simpel on 2006-07-12
yea, i did just that and it seemed to have solved the problem! hooray! 

Thanks for the help from everybody though!

---

