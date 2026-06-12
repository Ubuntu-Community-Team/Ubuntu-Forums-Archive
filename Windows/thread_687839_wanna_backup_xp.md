---
title: "wanna backup xp"
date: 2008-02-04
forum: Windows
---

### Post by tocilog on 2008-02-04
i was looking for a reliable program to back up windows xp to my external harddrive, but i found more questions instead. from what i read, taking a snapshop of the harddrive is what i would like to do, instead of just putting each file individually onto the harddrive. can anyone recommend a good program that does that, but free?

by the way, im doing this because im planning on dual booting ubuntu with xp.

---

### Post by aysiu on 2008-02-04
Well, the two obvious ones are Acronis True Image and Symantec Ghost, but since you want it to be free, your best bet may be [PartImage](http://www.partimage.org/Supported-Filesystems) with this caveat: > **The NTFS (Windows NT File System) is currently not fully supported:** this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after. If there is a problem when saving, an error message will be shown and you won't be able to continue. If you have successfully saved an NTFS NTFS partition, you shouldn't have problems as you restore it (except in the case of bugs). Then the best way is to try to save a partition to know if it is possible. If not, try to defragment it with diskeeper or another tool, and try to saving the partition again.

---

### Post by LaRoza on 2008-02-04
You can try Clonezilla, it can do partitions and entire disks.

See the link in my sig.

---

### Post by r76 on 2008-02-05
I haven't tried clonezilla, but have successfully used Partimage following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=287522").  Successfully, as in I have restored a good running system from said backups - not just made them in the first place.  However, as aysiu says Partimage comes with that NTFS disclaimer but I haven't personally found it a problem.  I have heard that good defragmentation before backup using this method may help, so I always do that. :)

---

