---
title: "Problem spinning disks down"
date: 2012-12-09
forum: Server Platforms
---

### Post by MadsRC on 2012-12-09
I have a server, with 2 data disks, pooled into one pool in /mnt/storage using aufs.

Then I configured disk spindown with following this site:
[http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)

Also, I have smartmontools configured.

Disk spindown worked a couple of days ago, but after I tingled a bit with the server (installing transmission, uninstalling transmission, installing deluge, creating a few scripts) the disk have stopped spinning down.

Does anyone know how to check why the disks isn't spinning down?
Or does anyone have an idea why my disks isn't spinning down?

---

### Post by rubylaser on 2012-12-09
Some Torrent deamons will occasionally access the disks they use as their destination even when they aren't downloading.  Do you have any of those disks setup as the destination?  Also,  if you have smartmontools installed, you'll want to set the files up as I have shown.

---

