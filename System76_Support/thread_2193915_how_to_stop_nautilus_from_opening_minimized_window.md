---
title: "how to stop nautilus from opening minimized window on sd card insertion"
date: 2013-12-15
forum: System76 Support
---

### Post by system76panp9 on 2013-12-15
I am running Nautilus on Ubuntu 13.04 System 76 panp 9 laptop
I have the options for media-handling in gsettings as false for automount and automount open
nevertheless, whenever I insert an SD card into the slot on the side of the laptop,
a minimized Nautilus window appears on my screen and when I unminimize it I discover
that it has opened a directory called /media/primary/NO LABEL which is displaying the
directory structure of the SD card drive
I would really really like to stop this from happening anymore and mount the drive myself
and for instance access it via the terminal instead of having the stupid Nautilus window
present itself when it is not wanted
from everything I have read, the gsettings for media-handling are exactly what is supposed
to prevent this, so I cannot figure out what it is that I am missing here
if there is no other way, maybe I could hard code the mount points for at least the drives
I am using often in /etc/fstab, and that might preempt Nautilus deciding it needs to mount
these media?
please, any help would be greatly appreciated

---

