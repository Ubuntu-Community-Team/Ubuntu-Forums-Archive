---
title: "Another backup question"
date: 2008-08-05
forum: Server Platforms
---

### Post by MountainX on 2008-08-05
I would like to "clone" (well, not exactly *clone*) the OS and boot partitions on a server that has Hardy installed on two 74 GB WD raptors as follows:

sda: /boot and /
sdb: /var, /tmp and swap

(/home is on a separate drive, and I'm not concerned about it for this question.)

On this server, I can insert an IDE drive with a removable drive tray. **I would like to make a single IDE drive that contains all the contents of sda and sdb and that will boot this server in the event of a failure of sda or sdb.**

How would I go about this? (All partitions except /boot are encrypted, btw.)

The IDE drive will probably be a smaller drive, say 40 GB (something I have on hand already). 40 GB is enough to hold all the data on sda and sdb, but it is obviously not enough to hold full images of both these.

BTW, I also hope to make a DVD image of the operating system and boot partition. Again, I could use some suggestions on how to ensure that this DVD backup will work when/if it is needed.

Thanks.

---

### Post by scorp123 on 2008-08-06
Works for cloning too:

"How to backup your stuff UNIX-style"
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

---

### Post by MountainX on 2008-08-06
> **scorp123 said:**
> Works for cloning too:

"How to backup your stuff UNIX-style"
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

That looks like an awesome how-to. Thank you!

My first step will be to get rid of the UUID's as you suggest. I'll keep working through your tutorial. It is just what I wanted. :)

---

### Post by scorp123 on 2008-08-06
> **MountainX said:**
> That looks like an awesome how-to. Thank you! Well ... you could thank by hitting the "Thank you" button ;)

---

