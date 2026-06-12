---
title: "Unable to execute script that's in flash drive?"
date: 2016-09-26
forum: The Cafe
---

### Post by KayeNg on 2016-09-26
I've read a few articles on it but I'm still not sure if it's possible or not.  Is it or is it not possible to run a script in flash drive? I'm trying to run bluegriffon from my flash drive but it won't run and the permissions can't be changed.

---

### Post by mJayk on 2016-09-26
it should be possible first thing to try is 

    sh /media/path/to/file.sh

or you could always just copy it to home and run it from there.

---

### Post by &amp;KyT$0P# on 2016-09-26
What filesystem is this flash drive?

---

### Post by KayeNg on 2016-09-29
mJayk, come to think of it, I'm not sure if it's a script, it does not have the .sh extension, it is simply named "bluegriffon", but normally if I copy it to home and run it from there (as you suggest), I simply double click it, then a window would appear with the options "Execute", "Execute in Terminal", "Open" and "Cancel", then I would click Execute and the program (bluegriffon) would run.

But when the entire directory is in a flash drive, if I double click "bluegriffon", it simply opens with Leafpad (text editor in Lubuntu).

halogen2, the filesystem is fat32.

---

### Post by &amp;KyT$0P# on 2016-09-29
> **KayeNg said:**
> halogen2, the filesystem is fat32.
I don't think fat32 supports Unix permissions.  That being said, my EFI partition has files that are listed as executable...

What is the permissions of the mountpoint, when mounted and when not mounted?

---

