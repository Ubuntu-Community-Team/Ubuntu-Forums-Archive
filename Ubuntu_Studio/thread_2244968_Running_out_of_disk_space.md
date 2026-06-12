---
title: "Running out of disk space"
date: 2014-09-20
forum: Ubuntu Studio
---

### Post by davidgrz on 2014-09-20
I keep getting a notification that I am running out of disk space. Says I have like 355 megabytes left. I am not sure what to do about that. Can I combine 2 partitions or something?

[[img]http://www.zimagez.com/miniature/screenshot-09202014-013403am.php[/img]](http://www.zimagez.com/zimage/screenshot-09202014-013403am.php)

[http://www.zimagez.com/zimage/screenshot-09202014-013403am.php](http://www.zimagez.com/zimage/screenshot-09202014-013403am.php)

Any ideas?

---

### Post by mikewhatever on 2014-09-20
Before combining partitions, you should probably investigate what's taking up all the space. You forgot to mention which partition is full, so I'll assume it's /dev/sdb7. 
Try running <du -s /* 2>/dev/null | sort -nr> as a quick way to see where most of the free space has gone.

To quickly free some space, run the following:

<sudo apt-get clean> to clean cached installation packages

<dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs apt-get purge> to remove old kernels and headers

<sudo tune2fs -m 1 /dev/sdb7> #to reduce the number of reserved blocks

---

