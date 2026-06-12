---
title: "Taking care of HD"
date: 2014-05-18
forum: The Cafe
---

### Post by LastDino on 2014-05-18
Well, I'm not really a technically involved person with computers beyond my curious nature, so I find this as a right time to clear some clouds in my head about the subject.

I've been quite literally abusing my 1TB HD by making various partition schemes with different type of partitions in order to make it duel/triple boot, and sometimes simply testing the partition system out by making one for heck of it. I'm curious because recently, on my test machine. Grub2 on fedora and Manjaro dual boot has been indicating I've ext2 ''/'' partition even though it is ext4 (it is yet to be seen if this is problem with grub or disk itself).
[ATTACH=CONFIG]253280[/ATTACH]

 I also see lot of people suggesting chkdisk and defragmenting on regular basis to new users. 
Few years ago, some know how to guy told me that it is not that much of necessity to run chkdisk or defragmenting if you're formatting the whole disk more than ''occasionally''. Naturally, by the shear amount of time taken by these processes, it is quite the turn off and I go with the easy way out.
This begs for question; what is true and what is not?

How should one who is into doing what I do (basically abuse) with my HD should make it live longer? Please explain with little bit of technical reasoning, mind you, I'm not that knowledgeable myself.
It is also appreciated if you can mention few tools which are efficient in doing the mentioned job if necessary.

---

### Post by ssam on 2014-05-19
The actual hard disk is not even aware of partitions, its just 1s and 0s being written to it, so it should have no effect on the disk life.

Fragmentation just means that due to space constraints individual files end up spread around the disk. This will slow access to those files, because the disk has to gather up the data from multiple places. How bad it is depends on the file system you use (modern systems like ext4 have techniques to reduce fragmentation), how full the disk is (if there is lots of free space then the filesystem can find continuous space for a new file) and usage (actions that change the size of an existing file are more likely to cause fragmentation).

If you regularly create new partitions, then that will remove the fragmentation. Tools for de-fragmenting are specific to the filesystem type.

---

### Post by HiImTye on 2014-05-21
if you're using an ext file system, then you'll only need to worry about fragmentation as your partition approaches capacity. that said, fsck automatically runs in frequency specified by the 'pass' option in fstab, so you should use that option to specify the frequency the partition is checked, with '1' for any system partitions, and '2' for any storage/backup partitions.

ext is backwards compatible so it's likely set to ext2 in the fstab, I'd check to make sure and change it as appropriate

---

