---
title: "Partition - need to clear the dir_index attrib."
date: 2008-02-10
forum: System76 Support
---

### Post by Martjc on 2008-02-10
I need to shrink the partition set as ext3.  I have been told that this is the way to do it.

in Linux single-user mode
type the following:
umount /dev/xxx
tune2fs -0dir_index /dev/xxx

where xxx is the name of the file system.

My questions:

What is single user mode?

How do I find out what to use in xxx?

Do I need to be root?
How do I accomplish this?

Any help appreciated.  Am a total novice to ubuntu.

---

### Post by thomasaaron on 2008-02-11
I'd recommend following the instructions at the beginning of this tutorial for re-sizing partitions.

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

