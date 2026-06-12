---
title: "partition security"
date: 2010-04-22
forum: Security
---

### Post by TomAbada on 2010-04-22
hi all
im new here so be  gentle

i need a way to monitor a certain partition / folder
to see if any changes has made

is there anyway of doing that ?

---

### Post by Rubi1200 on 2010-04-22
If you don't mind me asking, why do you need to monitor the partition/folder? Is it on a Windows partition and what is your intended goal?
I suggest you first read bodhi.zazen's security stickies and see if your question/needs are answered there.
Good luck and welcome to the world of Linux.

---

### Post by cdenley on 2010-04-22
If you want to monitor all filesystem operations performed:
```

man inotify

```
If you're monitoring temporary files and browser caches, though, there might be too much useless data to make this monitoring effective.

If you want to see any files which have changed, you would need to maintain a database of files with checksums, then re-compute and compare periodically. There are tools which do this for critical system files, but I don't know of one that does this for an entire filesystem/directory. Depending on the size of the filesystem/directory, it might be impractical to read all the data and compute checksums for every file. You can look at timestamps, but if this is for security, I don't think that is a reliable way to monitor for malicious tampering.

---

### Post by HermanAB on 2010-04-22
If you don't want it to change, mount it read only.

Otherwise you can find changed files with tar, by looking for the archive bit.

---

### Post by bodhi.zazen on 2010-04-22
> **TomAbada said:**
> hi all
im new here so be  gentle

i need a way to monitor a certain partition / folder
to see if any changes has made

is there anyway of doing that ?

Depending on what you are looking for, sounds like a task for tripwire or aide.

---

