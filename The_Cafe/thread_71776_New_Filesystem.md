---
title: "New Filesystem"
date: 2005-10-04
forum: The Cafe
---

### Post by KingBahamut on 2005-10-04
An R&D affiliate of the world's largest telephone company has achieved a stable release of a new Linux file system said to improve reliability over conventional Linux file systems, and offer performance advantages over Solaris's UFS file system. NILFS 1.0 (new implementation of a log-structured file system) is available now from NTT Labs (Nippon Telegraph and Telephone's Cyber Space Laboratories).

External Links
[http://www.linuxdevices.com/news/NS9521569196.html](http://www.linuxdevices.com/news/NS9521569196.html)

Log-structured filesystems write down all data in a continuous log-like format that is only appended to, never overwritten. The approach is said to reduce seek times, as well as minimizing the kind of data loss that occurs with conventional Linux filesystems. 

What are the implications here? I find this concept to be if anything interesting. Is it a possible replacement for reiser , ext, or xfs...probably not. But the implications in how it functions might present other possibilities in the way a file system functions. 

Of course the obvious question that comes to mind is , what happens when it gets to the end?

---

### Post by Kyral on 2005-10-04
I don't claim to know anything about Filesystems aside from what makes a Journaled FS different than a non-Journaled FS, so I'm prolly gonna stick with my ext3/ReiserFS combo

---

### Post by KingBahamut on 2005-10-04
Kyral......not meant to get users to make a switch, but merely to intellectualize the concept. Will it mean change for us? It might, but most certainly not in the immediate future.

---

### Post by UbuWu on 2005-10-04
No it won't. See this slashdot comment: [http://linux.slashdot.org/comments.pl?sid=164222&cid=13712976](http://linux.slashdot.org/comments.pl?sid=164222&cid=13712976)

---

### Post by super on 2005-10-04
i don't know too much about filesystems, but wouldn't this approach lead to major disk fragmentation eventually? and what happens when a file is to be deleted?

hmm.. i guess i'll have to read up a bit on this.:???:

---

### Post by Kyral on 2005-10-04
KB I'm just saying that Ext3 and ReiserFS have never failed me (I was quite impressed during one period last week were my overclocking attempts let to multiple sudden reboots in the middle of the boot process, something that should have really screwed up the Filesystems, btu a quick ReiserFsck to make sure everything was okay cleaned everything up :D)

---

