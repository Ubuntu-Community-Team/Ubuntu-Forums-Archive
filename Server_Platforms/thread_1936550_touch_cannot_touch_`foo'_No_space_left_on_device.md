---
title: "touch: cannot touch `foo': No space left on device"
date: 2012-03-06
forum: Server Platforms
---

### Post by GS340 on 2012-03-06
HI,

I can't seem to figure out this problem.  Partition shows free space but I can't write files to it.  I delete 1 file I can write 1 file.

df -h  
/dev/sda1              28T   25T  3.2T  89% /data


df -i 
/dev/sda1            5858917952  340288 5858577664    1% /data

df -hi
/dev/sda1               5.5G    333K    5.5G    1% /data

Don't think it's inode issue but i'm not sure what else to check.. Please advise.

thank you in advance.

---

### Post by aeiah on 2012-03-06
> 
df -h 
/dev/sda1 28**T** 25**T** 3.2**T** 89% /data


so your partition is reporting that it is 28 Terabytes in size. is this an obscenely massive array, or is this an error?

> 
df -hi
/dev/sda1 5.5G 333K 5.5G 1% /data


im not too up on inodes, but i would think you should be expecting more than 1% inode use if your drive has anything on it. this might not be true if your partition is indeed 28TB. have you ran a filesystem check?

---

### Post by GS340 on 2012-03-06
The array size is correct.   Issue started when the partition filled up yesterday and I deleted the oldest data and today 89% seems to be the max the partition will hold.

Running xfs_check now...  Should take a while.

---

### Post by GS340 on 2012-03-06
xfs_repair -n /dev/sda1 came back with no errors.

mounted the the partition with the -o inode64 option and I can write files now.  I need to read up more on the inodes and inode64 with xfs.

so, it seems to be working again.

If I'm missing something please post.

thank you

---

