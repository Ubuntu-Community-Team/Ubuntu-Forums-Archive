---
title: "incron doesn't work"
date: 2008-12-17
forum: Server Platforms
---

### Post by leon.hh on 2008-12-17
Hi, here i am again. This time I wanted to implement some fancy features on my file server and I thought that it was a good idea to avoid users to upload media type files (mp3, avi, and so on) but running a process every night looking for this kind of files could be a performance issue (due to there will be millions of files and dozens of Gigabytes, and the process would have to check the entire filesystem once and again every night).

So I found a fancy way to setup this restriction installing incron.

Here the problem begin: I set this line through incrontab

```
/data IN_CREATE,IN_MOVED_TO script $@/$#
```

I ran every kind of tests but nothing happens, the program "script" never raises, instead of script I used several program including the OS one (like rm, touch, etc.) but nothing...

Help please!

---

### Post by leon.hh on 2009-02-10
Easy solution:

inotify needs to be specifically declare during the system boot, then I modified the menu.lst as follows:

kernel          /boot/vmlinuz-2.6.26-1-686 root=/dev/sda1 ro *inotify=yes*

And that's it, incron it's now working perfectly!

---

