---
title: "Complex Backup"
date: 2007-05-24
forum: Server Platforms
---

### Post by scott_ttocs46 on 2007-05-24
Hi all,

     I have a file server with three disks of varying sizes that contain 550 GB of irreplaceable data. I also have another file server I want to act as a backup for the first file server. It has a 630GB capacity on five disks of varying sized. Both are on a 100MB LAN. So, a slow, leaky sort of backup is preferable. The file table changes often. Being able to sync or update instead of completely replacing the data is a must.

Any ideas? I have no idea where to start.

Regards,
Scott

---

### Post by craigp84 on 2007-05-25
Hi scott_ttocs46,

> irreplaceable data

You need more than just a second fileserver :) Get a proper back sorted out or it'll bite you.

Rsnapshot sounds like just the thing for you. Sudo apt-get install rsnapshot - it's a doddle to setup. Also makes restoring pretty easy.

Hope this helps,

-c

---

### Post by Chayak on 2007-05-25
Well if your data is that vital and you don't mind spending the money Acronis true image has yet to fail me.  Though on my home servers I have an hourly cron job to rsync to a backup server and from there at midnight every night it backs up to a hot swap hard drive.

---

