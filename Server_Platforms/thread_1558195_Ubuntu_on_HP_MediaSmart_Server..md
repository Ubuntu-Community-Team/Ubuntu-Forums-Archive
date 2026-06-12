---
title: "Ubuntu on HP MediaSmart Server."
date: 2010-08-21
forum: Server Platforms
---

### Post by Off Topic on 2010-08-21
OK,  Ive got this working somewhat.  Ubuntu 10.04 on a HP Mediasmart Server.  It seems I may have wiped the flash drive embedded on the motherboard so I can no longer restore it with Windows Home Server.

I can remote in using SSH but not VNC which is fine for the moment.  The problem starts when I try to add hard drives to the unit.  It boots just fine with just the HD with the system on it,  but if I add an empty HD formatted NTFS the system may boot but I cant remote in to see,  I just cant get a connection.

What I need to do.

1. get the machine to boot with more then the file system hard drive installed and auto mount the other hard drives.  Ill figure out fstab later.

2.  Using the command line,  set up the Video folder for sharing,  video storage and streaming is all Im going to use this box for,  for the near future anyway.

---

### Post by Off Topic on 2010-08-29
Update.

I got Webmin installed,  something new to learn about.  Plan for the box for the foreseeable future is a video server,  far less glorious then its intended function but its what it is.

---

