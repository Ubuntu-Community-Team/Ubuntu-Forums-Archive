---
title: "File Accessed property"
date: 2014-04-28
forum: Security
---

### Post by jesjep on 2014-04-28
Hi,

I can see that file properties like "Modified" change whe the file is modified. However, what does the "Accessed" file property describe? It does not appear to change for example if I open the file.

---

### Post by untrustytahr on 2014-04-28
There are 3 times associated with linux files: atime (access time), mtime (modifed time), ctime (inode change time).

For performance reasons, some people turn off atime when the drive is mounted.

---

### Post by thnewguy on 2014-04-28
Accessed time (atime) should show you the last time someone opened the file. Anytime you open to read the file or change it, the file's access time should change. .... Unless changing access times had been disabled on your computer. A lot of people disable access time to reduce the number of times information on the disk is updated, or to improve performance.

Check the file /etc/fstab. It lists all drives that are automatically attached to your system. If one of the entries has "noatime" on the line, then it means access times have been disabled.

---

### Post by untrustytahr on 2014-04-28
> **thnewguy said:**
> Check the file /etc/fstab. It lists all drives that are automatically attached to your system. If one of the entries has "noatime" on the line, then it means access times have been disabled.
  

Or 'relatime' which is a hybrid between changing with every access and never changing.  Using noatime can break some applications.  It may be the default setting in Ubuntu, but I would have to look it up to be certain.

---

### Post by ant2ne on 2014-04-29
I always set noatime and I've not had it break anything, yet.

---

### Post by HermanAB on 2014-05-01
On most distros, relatime is the new default.  It will avoid writing unnecessarily to files that are cached or reside on SSDs.

---

