---
title: "The state of NTFS read/write in Linux"
date: 2006-10-10
forum: The Cafe
---

### Post by raublekick on 2006-10-10
I always thought that NTFS read/write was supposed to be unstable in Linux, especially write support. But lately I've been noticing a few distros that support NTFS read/write out of the box. I tried searching for info on it, but could only find a few guides on how to get read/write support, but nothing on whether it is at a good state now. 

So where is Linux on this issue?

---

### Post by maagimies on 2006-10-10
Well, there's [Ntfs-3g]("http://www.linux-ntfs.org/"), reading/writing has worked for me so far, but don't blame the coders if your harddrive grows a pair of arms and legs and tries to kill you :mrgreen:

---

### Post by PriceChild on 2006-10-10
As far as i'm aware... MS have NOT released details of the inner workings of ntfs.

This means that you may experience massive data loss using ntfs drivers in Linux.

You've been warned :)

---

### Post by raublekick on 2006-10-10
yeah, your comments are exactly what i've heard in the past. but for distros to be including it by default seems really weird if it's not stable.

---

### Post by 3rdalbum on 2006-10-10
It's recently gone into a beta version, which means it's nearly finished cooking. Some of the Puppy Linux developers have tested it, not had any problems, and decided that it's good enough to use.

---

### Post by The Noble on 2006-10-10
NTFS-3g has been working very well for quite a lot of people and is the main solution to this ntfs problem. The other distros are using ntfs-3g for the read/write and quite a few tests have been run (unofficially of course) to show that it is the answer currently.

---

### Post by econobeing on 2006-10-10
my external was NTFS(i didn't know because i never checked), but then it started getting screwy. like about a week ago 5 folders appeared in the root of it called "LINUXI~1" i couldn't go into them or delete them. then all of the sudden i lost write access to the drive while in linux. then i started seeing files called "UBC[square root symbol][two squares][other junk]" all over it, which i couldn't delete.

yesterday i reformatted and gave linux a 32GB FAT32 partition(wierd since 95% of the time i'm on linux...) and kept the other 200~ as NTFS.

summary: worked fine for a while, then started acting wierd and crapped out.

---

