---
title: "Rsync permissions"
date: 2014-02-22
forum: Server Platforms
---

### Post by david_brown on 2014-02-22
Hi, I'm new to ubuntu and on a steep learning curve but getting there :)

I have recycled my old PC as a home server and am trying to set up some backup tasks with luckybackup. I have an external USB disk that I want to back up some files to. It's mounted and shared and can be used by Windows. The error message when I run luckybackup is 

operation not permitted (1) Rsync: failed to set permissions on "/media/lacie/pictures/picture.jpg"

The way it's mounted in /etc/fstab is


UUID=6853-5BA9 /media/lacie vfat auto rw user 0 0

I am using luckybackup to pull data from another drive to backup to the servers internal drive sucessfully, so the problem seems to be writing to the usb mounted lacie

Any ideas please?

---

### Post by david_brown on 2014-02-22
Prob solved - told luckybackup destination was fat/ntfs in advanced options and it's running fine :)

---

