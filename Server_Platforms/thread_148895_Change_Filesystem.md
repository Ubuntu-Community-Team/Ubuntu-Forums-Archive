---
title: "Change Filesystem"
date: 2006-03-22
forum: Server Platforms
---

### Post by rbrugman on 2006-03-22
This is kind of a long shot, but is there any way to change the filesystem of a volume group?  On my server, I am using ReiserFS.  It used to be fine, but now my group has grown to over 1TB and Reiser is a bit slow.  If I have to reformat I'll just have to live with it, because I don't happen to have another Terrabyte of hard drive space handy, but if there was a semi-easy way of changing it, I'd go for it.


Thanks,
Robert

---

### Post by adamkane on 2006-03-22
You need to give more details.

How many discs in the group? Is / part of the LVM? What is the size of the group? How full is the group?

---

### Post by rbrugman on 2006-03-22
[QUOTE=adamkane]You need to give more details.

How many in the group? Is / part of the LVM? What is the size of the group? How full is the group?[/QUOTE]

There are three partitions spanning three different hard drives.  The group is 1080GB total and 64% is used.  Mainly is what I'm asking is whether or not changing the filesystem would even be worth it.  Would I gain that much of changing it?  In reality, I'm limited by my network interface which is only 100Mb/sec.  Since the server is used for backing up my other computers I don't really know if changing it would be worth the hassle.

Thanks,
Robert

---

