---
title: "filesystems"
date: 2005-11-19
forum: The Cafe
---

### Post by adam.tropics on 2005-11-19
Is the ext3 file system 'self-maintaining' in the sense of performance?, for example fat32 is not. They told us ntfs was, but then it turned out it apparently wasn't! So what's the go? and why is rheiser better, or is it?

---

### Post by xequence on 2005-11-20
Self maintaining? If you are asking if it gets fragmented, then no, it doesent. You dont need to use any defragmenting tools.

---

### Post by Brunellus on 2005-11-20
reiser is optimized to be faster for lots of small files, which, coincidentally, describes a typical linux install.  there have been some gripes as to reiser's stability, but I've been running reiser for a year and haven't noticed anything untoward.

xfs is optimized for writing and deleting very large files quickly;  I believe it was originally developed by SGI for use in video editing, and excels with media recording, playback, and that sort of thing.

---

### Post by Cyril on 2005-11-20
ext3 is very resistant to fragmentation but it does get fragmented.

---

### Post by Carbon Copy Man on 2005-11-20
Hmmm. Is anyone able to offer a semi-technical explanation of why ext3 doesn't fragment (much)? I'm curious.

---

### Post by BWF89 on 2005-11-20
So ext3 is slower and it doesn't get fragmented while ReiserFS is faster but does.

How good are the Linux defragmenting tools at restoring the system to it's origional speed?

---

### Post by BoyOfDestiny on 2005-11-20
[QUOTE=BWF89]So ext3 is slower and it doesn't get fragmented while ReiserFS is faster but does.

How good are the Linux defragmenting tools at restoring the system to it's origional speed?[/QUOTE]


No. Both ext3 and reiser do not need to be defragged manually. However, if the disk is full, some fragmentation is unavoidable.

For those with questions go to wikipedia:

[http://en.wikipedia.org/wiki/Reiserfs](http://en.wikipedia.org/wiki/Reiserfs)

A lot better than circular reasoning...

EDIT: Great link here: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

