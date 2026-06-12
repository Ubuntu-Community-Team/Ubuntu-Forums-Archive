---
title: "Jaunty corrupt filesystem on fresh install? daru3"
date: 2009-05-05
forum: System76 Support
---

### Post by AmishSexy on 2009-05-05
I've tried installing Jaunty several times on my darter ultra 3 and each time the drive eventually turns to read only and then become corrupted. On reboot, X server fails to start and fsck is killed. I've tried using the alternate install and multiple different partition settings (so it can't be ext3 or ext4's fault right?). I've tried e2fsck several times . I initially thought this was my hard drive's fault so I bought a new one but the same issues occur. I'm willing to switch distros if its an Ubuntu exclusive issue but I'd prefer to stay with ubuntu. Thanks!

---

### Post by thomasaaron on 2009-05-05
First, don't use ext4 yet. Use ext3. While I've not seen them personally, this...

[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

...indicates ext4 may be unstable.

Second, when you partition, make sure you select the 'format' checkbox.

EDIT: Also, are you using an SSD?

---

### Post by thomasaaron on 2009-05-06
Try disabling tracker and see if you still get a corrupted filesystem.

[http://www.google.com/search?q=jaunty+tracker+corrupts+filesystem&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=jaunty+tracker+corrupts+filesystem&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by thomasaaron on 2009-05-06
Actually, this post is better. Also includes work-arounds and points to bug reports.

[http://ubuntuforums.org/showthread.php?t=1138029](http://ubuntuforums.org/showthread.php?t=1138029)

---

