---
title: "What would you do"
date: 2010-03-31
forum: The Cafe
---

### Post by clancymf on 2010-03-31
I have just added an additional 1 tb drive to my system. Before I upgrade to 10.04 which should i choose to put my /home folder on and which should contain my sytem files and backup folder:

1. 1 TB 16 mb cache; or
2. 1 TB 64 mb cache

Also should I format the drive ext4 or ext3?

Thanks for your feedback!

---

### Post by blueshiftoverwatch on 2010-03-31
> **clancymf said:**
> Also should I format the drive ext4 or ext3?
Google is switching over from Ext2 to Ext4. So I'd take that as an indication that it's pretty stable.

---

### Post by clancymf on 2010-03-31
Thats good to know!  Thanks for taking the time to respond.

---

### Post by undecim on 2010-03-31
Go with the 16 MB cache for your home folder and 64 MB cache for your system files. Generally, higher cache=more speed, and performance is affected by your system files more than your home files.

---

### Post by descendent87 on 2010-03-31
Why not put both / and /home on the drive with 64mb cache? 10GB for / and then the rest for /home?

---

### Post by undecim on 2010-03-31
You could set them up as a RAID0 for some performance boost. But be warned that if one of them goes out, the data on the other one will become worthless.

Another alternative is to use RAID1, which gives you half the storage space, but if one of them goes out, the other one still has your data. It also gives you slightly faster read speed (but slower write)

Or even better yet, partition them identically, set up swap and / as RAID0, and your home partition as RAID1 (faster access to swap and system files, and redundancy for your important files in /home/)

---

