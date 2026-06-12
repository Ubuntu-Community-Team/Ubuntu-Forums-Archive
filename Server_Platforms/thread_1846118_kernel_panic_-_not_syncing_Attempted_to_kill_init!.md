---
title: "kernel panic - not syncing: Attempted to kill init!"
date: 2011-09-18
forum: Server Platforms
---

### Post by keaarori on 2011-09-18
Hello, I am having a problem on my rented server box, What happened when this issue occurred was all the programs on the ubuntu box suddenly came up with error "file not found" or something around that even the command prompt, this all happened after we were out for an hour.

More specifics

- Server does not start up with error kernel panic - not syncing: Attempted to kill init!

I have attempted to contact support with the following responce
```


The technicians have indicated that the server has shown to have a "Kernel Panic".

The server is currently in Recovery Mode with the password : *****

You may end the Recovery Mode through your customer panel under : Hardware > Recovery > "Cancel Recovery".

With the Recovery System, you should be able to perform a fsck or other procedure to correct the issue.

Thank you for your time. Please do not hesitate to contact us for any further questions or problems.
Our Support Team will be happy to assist you.

Kind Regards
Antoine Meijer

```

Fsck Results


root@xray809:~# fsck -f /dev/md0
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md0: 37/24384 files (8.1% non-contiguous), 35499/97536 blocks


root@xray809:/# fsck -f /dev/md1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
(Putty crashed on this one rerunning)


I am quite new to anything to do with this recovery mode, but not new to computing, any helps would be greatly appreciated, thanks!

---

