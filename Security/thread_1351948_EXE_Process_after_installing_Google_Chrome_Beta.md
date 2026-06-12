---
title: "EXE Process after installing Google Chrome Beta"
date: 2009-12-11
forum: Security
---

### Post by UltraZone on 2009-12-11
Google released their Chrome Beta browser a few days ago as everyone and their grandmother knows and I installed it.  Now after a while of having Chrome open a process named EXE comes up.  Of course processes named Chrome are open, so having this EXE process pop out of nowhere is freaking me out.  I also have WINE installed, with Window's version of Firefox installed there (did this a month ago for testing purposes),  making this situation highly TABOO on my puter.  I googled my way across the interwebs but nothing significant comes up regarding this.  The process ends once Chrome is closed and does not seem to come up on its own.  Anybody know what's going on here?

---

### Post by spetey on 2009-12-11
I get the same process and am also curious.  Chrome 4.0.249.30 on Ubuntu 9.10.  Benign?

---

### Post by rishabh_destiny on 2009-12-11
Debian file is available for direct download

---

### Post by Alpha UMa on 2009-12-11
I killed the EXE process and Flash stopped working in Chrome

---

### Post by hussong on 2009-12-26
Definitely seems related to flash in chrome.  I had a myspace page open in a background tab and exe was hogging 45% of CPU.  After closing the tab, the process disappeared from top.

---

### Post by lsiden on 2010-01-06
Case solved: I opened a terminal console and typed "killall exe".  Immediately, Chrome responded with pop-up tabs notifying me that all of my extensions just quit!  Fortunately, each tab has a button to restart it.  Very nice!  :)

---

### Post by 3rdalbum on 2010-01-06
I noticed this as well, but when I checked this "exe" file was a symlink to /usr/bin/file. I didn't know it was related to Chrome though.

---

### Post by geira on 2010-01-26
> **3rdalbum said:**
> I noticed this as well, but when I checked this "exe" file was a symlink to /usr/bin/file. I didn't know it was related to Chrome though.

You're referring to **/proc/self/exe**, which has no relation to the **exe** process started by Chrome. The **/proc** directory is a virtual filesystem showing running processes and has nothing to do with what's on your hard disk. **exe** is a system call which returns the location of the running process, while **/opt/self** is just shorthand for the current process, which will vary depending on whatever binary you're calling it from.

```
geira:~$ ls -l /proc/self/exe 
lrwxrwxrwx 1 geira geira 0 2010-01-26 11:55 /proc/self/exe -> /bin/ls

geira:~$ file /proc/self/exe 
/proc/self/exe: symbolic link to `/usr/bin/file'

geira:~$ stat /proc/self/exe
  File: `/proc/self/exe' -> `/usr/bin/stat'
  Size: 0               Blocks: 0          IO Block: 1024   symbolic link
Device: 3h/3d   Inode: 73110954    Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (43438/   geira)   Gid: (43438/   geira)
Access: 2010-01-26 12:01:01.362727528 +0100
Modify: 2010-01-26 12:01:01.362727528 +0100
Change: 2010-01-26 12:01:01.362727528 +0100

```

---

### Post by leeds_shrew on 2010-02-02
I'm going to start a new thread about this because I'm having an issue with it. Search my posts to find it if any good comes of it!

---

