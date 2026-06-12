---
title: "My experience with the klogd logging bug"
date: 2009-01-21
forum: System76 Support
---

### Post by nailbmb on 2009-01-21
I've been suffering from _[this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)_ for the past week or so on my DARU3.  The bug has been mentioned on the System76 forum in _[this](http://ubuntuforums.org/showthread.php?t=1010145&highlight=klogd)_ thread.

My system was very stable up until recently.  Things got really bad in the last few days; multiple reboots would inevitably lead to either a hosed klogd instance or a kernel panic.  I determined that the issue was related to my wireless connection.  Using wireless --> klogd/kernel panic.  Using wired network --> stable system.

The bug report mentions that the problem is fixed in kernel version 2.6.27-10.  I was running 2.6.27-9, so when I finally got fed up with my system's spotty stability, I upgraded to the latest kernel (2.6.27-11).

So far so good!  The system has been stable for about 25 minutes, which is better than could be expected just prior to the upgrade.  Dunno if there is another solution for the issue, but this was a life saver for me.

---

### Post by Lee_Machine on 2009-01-22
It's usually best to always upgrade to the newest stable kernel. Most of the time 50% of the changes/addons are either new drivers or bug fixes for old ones.

Now I never had any problems with any of my other Linux boxes and using the proposed Kernels, but with my S76 Pangolin Performance I have. All of which was fixed when the official version comes out. 

Most recently being screen brightness adjustments stopped working. Which was fixed when the official -11 came out.

---

