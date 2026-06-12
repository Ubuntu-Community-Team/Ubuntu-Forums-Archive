---
title: "How does Linux really know what user I am?"
date: 2010-04-14
forum: Security
---

### Post by GenePayne on 2010-04-14
I have a USB drive that I use both at home and at work (Ubuntu both places). My username is different on my work machine than my home machine, and I always have to change the owner of all the files on the drive to match whichever computer I'm on, or I run into permissions problems.

If I had the same username both at home and at work, would it know the difference? Or is there a user ID or some other code/ID that Linux uses to identify a user?

---

### Post by Jive Turkey on 2010-04-14
I might be way off, but I think that linux gives individual files uid and gid values that are numeric and those are resolved to actual user and group names by the local OS.  They could coincide, and they could be tinkered with but it might not be very straightforward.  If your flash drive is fat32 formatted then this might not be the case at all, I only have a vague idea what I'm talking about.

---

### Post by HermanAB on 2010-04-14
Your UID and GID is a number that usually starts at 500 when new accounts are created.  

So for least hassle when moving disk drives around, you got to change one of the machines so that your UID and GID are the same on both.

---

### Post by gradinaruvasile on 2010-04-14
I use vfat for USBs. No problems here as the file system doesnt have this feature and its compatible with other OS es (read Windows) too.

---

### Post by GenePayne on 2010-04-23
Thanks for the replies. I think I solved the problem by changing my user ID (uid) on one machine to match the other.

```
id myusername
usermod -u 600 myusername
id myusername
```

I had to do this after I logged into a different user in a terminal session (no x server).

So far this is working well without me having to recursively change ownership of all files/folders every time I move to the other computer. This would not have been a problem if I left it formatted as FAT instead of ext2, but I like having the advantages of permissions and setting files as executable.

---

