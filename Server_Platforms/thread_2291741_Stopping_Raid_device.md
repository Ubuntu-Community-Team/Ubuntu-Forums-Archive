---
title: "Stopping Raid device"
date: 2015-08-22
forum: Server Platforms
---

### Post by rawrzor on 2015-08-22
Hello,

I currently have a situation and I am not sure what to do.
I have a production server where all the diskspace is vanishing into thin air.

df -h shows:

```
Filesystem      Size  Used Avail Use% Mounted on
rootfs           20G   17G  1.7G  92% /
/dev/root        20G   17G  1.7G  92% /
devtmpfs        7.8G     0  7.8G   0% /dev
tmpfs           1.6G  268K  1.6G   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           3.4G     0  3.4G   0% /dev/shm
/dev/md3        1.8T  2.4G  1.7T   1% /home
```

However when I check where all the diskspace is going with du -h --max-depth=1 it adds up to approximately 4.4gb.

I have a software raid running which seems to be the problem.

fdisk -l shows:

```
Disk /dev/md3: 1978.9 GB, 1978886193152 bytes
2 heads, 4 sectors/track, 483126512 cylinders, total 3865012096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md2: 21.0 GB, 20970405888 bytes
2 heads, 4 sectors/track, 5119728 cylinders, total 40957824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table
```


Md2 appears to be filling up the diskspace.

What happens if I unmount md2, will the OS continue to function without data loss? What other solutions are there to this problem?

---

### Post by howefield on 2015-08-22
Thread moved to the "*Server Platforms*" forums.

---

### Post by rawrzor on 2015-08-22
For all who might encounter the same issue, i found the  issue moments after the creation of the topic.

I ended up finding this thread [http://unix.stackexchange.com/questions/113840/whats-eating-my-disk-space](http://unix.stackexchange.com/questions/113840/whats-eating-my-disk-space)
So i ran the command 
find /proc/ -mindepth 3 -maxdepth 3 \
-regex '/proc/[1-9][0-9]*/fd/[1-9][0-9]*' -type l -lname '*(deleted)' \
-printf '%p\n     %l\n' 2>/dev/null

and I found out that theres a huge amount of deleted logfiles that were secretly eating all my diskspace. I restarted Apache and the problem was solved.

---

### Post by ajgreeny on 2015-08-22
Brilliant!

To help out searchers looking for this in future please mark this thread as SOLVED from the Thread Tools menu at the top.

EDIT:
Don't worry, I've done that on your behalf, but in future please mark as solved when a solution has arrived.

---

