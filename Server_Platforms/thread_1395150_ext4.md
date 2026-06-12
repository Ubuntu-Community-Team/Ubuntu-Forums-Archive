---
title: "ext4"
date: 2010-01-31
forum: Server Platforms
---

### Post by Vegan on 2010-01-31
I have inquired before about ext4 vs ext3 and I am happy that the file length limitations of ext3 are history.

So I am now interested to know how many files I can stuff into a single folder, such as pics etc as I have a digital camera and the thing can crank out pics like mad.

I already have PHP code that scans the folder and generates HTML for me automatically, I can simply copy pics and poof they are on-line immediately. So how many pics can I post?

I have a nice fat 500GB disk to use so I am looking at a lot of pics and other graphics for my sites compared to the old text oriented object.

I have some pics now for specific pages, but I was thinking of a new page with pics of the hood.

---

### Post by falconindy on 2010-01-31
It's not entirely clear to me which FS you're asking about, so I'll just answer both...

In regard to Ext3:
> The maximum number of inodes (and hence the maximum number of files and directories) is set when the file system is created. If V is the volume size in bytes, then the default number of inodes is given by V/213 (or the number of blocks, whichever is less), and the minimum by V/223. The default was deemed sufficient for most applications. The max number of subdirectories in one directory is fixed to 32000.

In regard to Ext4: 4 billion. You are, however, limited to 64,000 subdirectories per directory.

---

