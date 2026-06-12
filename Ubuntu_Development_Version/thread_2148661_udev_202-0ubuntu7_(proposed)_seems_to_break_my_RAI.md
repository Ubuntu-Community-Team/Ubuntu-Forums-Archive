---
title: "udev 202-0ubuntu7 (proposed) seems to break my RAID boot seq..."
date: 2013-05-26
forum: Ubuntu Development Version
---

### Post by tista on 2013-05-26
Hi all,

Had someone guys tried proposed udev packages on some RAID machines?
Just now I only have a choice to downgrade that packages to "175-0ubuntu29"...:(

In a boot sequence, an initramfs seemed to fail to mount local RAID array (dual SSD on my VAIO Z21 series).
Or other words, maybe, udev 202 couldn't kick the dmraid scripts out?

Anyway I'm really relieved now to get back my saucy desktop... ;)

---

### Post by jfernyhough on 2013-05-26
Let Martin Pitt know. He needs test cases. (He's on G+ and posted about the new systemd stuff recently).

---

### Post by tista on 2013-05-28
Hi jfernyhough :)

Thanks for your advice.
So I've written a message to Martin on g+...
And now I'm sorting lots of logs in order. ;)

Best Regards,
Tista

**EDIT**
I've posted bug report to launchpad already..
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1185060]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1185060")

---

### Post by tista on 2013-05-29
Today I've confirmed Martin's fix to solve this issue... ;)
Yeah that's magic!?

Soon that commit would be applied into main repository, So you'd better to wait for the next version (maybe 202-0ubuntu9? or so)!!
Finally this thread got "solved".

Best Regards,
Tista

---

### Post by jfernyhough on 2013-05-29
Excellent news! It also means the system works. ;)

---

