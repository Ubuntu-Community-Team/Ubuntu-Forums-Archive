---
title: "Rsync problem with folder deletion"
date: 2011-04-17
forum: The Cafe
---

### Post by xtheunknown0 on 2011-04-17
Why doesn't rsync delete the 2010lectures folder and its contents on the USB when I run the following instruction?

rsync --log-file=rsynclog --progress --recursive --times --perms --links --delete --exclude-from='Documents/exclude.txt' --delete-excluded /home/xtheunknown0/ /media/usb1/

Here is my exclude.txt file
/Downloads
/Desktop/books
/Documents/uniit/2010lectures

Here is part of the latest rsync log file.

2011/04/13 19:21:24 [11837] cd+++++++++ Documents/uniit/2010lectures/
2011/04/13 19:21:24 [11837] cd+++++++++ Documents/uniit/2010lectures/programming/
2011/04/13 19:21:34 [11837] >f+++++++++ Documents/uniit/2010lectures/programming/1.m4v
2011/04/13 19:22:03 [11837] >f+++++++++ Documents/uniit/2010lectures/programming/10.m4v

xtheunknown0

---

### Post by xtheunknown0 on 2011-04-18
Bump

---

