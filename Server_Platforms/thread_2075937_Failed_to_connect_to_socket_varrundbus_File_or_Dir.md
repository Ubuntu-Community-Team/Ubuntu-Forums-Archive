---
title: "Failed to connect to socket /var/run/dbus: File or Directory does not exist"
date: 2012-10-24
forum: Server Platforms
---

### Post by greenrubberducky on 2012-10-24
Okay...I've read up a little on this bug: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")

Seems that my installation of 12.04 server had the same problem. On my first reboot, it halted and sat with a blinking cursor. 

Set the boot script to "nomodeset" and "verbose".

That's when I saw and googled the "failed to connect to socket /var/run/dbus" issue. Tried the fix that was shown in the 11.04 to 11.10 upgrade bug, but that didn't help me. 

It booted initially...is there a good way to basically give the server install a clean boot segment? 

dpkg --configure -a hasn't helped either.

---

