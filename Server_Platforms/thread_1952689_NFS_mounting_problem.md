---
title: "NFS mounting problem"
date: 2012-04-04
forum: Server Platforms
---

### Post by pepsifx357 on 2012-04-04
Hey all,

I've got a FreeNAS box setup serving me some hard drive space.

The problem that I am having with Ubuntu, is that the entries in fstab, that I made, seem to be creating icons of every mounted volume on the desktop.  Is there a way to keep it from doing that and still have automount on startup?

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,exec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3021cb8f-290c-46e4-9beb-7dbd0de5f649 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda2 during installation
UUID=1badf8f6-b1c7-43d8-af85-7742eaf6b97a none            swap    sw              0       0

#Remote Shares

#Documents
10.1.1.7:/mnt/HMS-Storage/Documents /home/ben/Documents nfs rw,hard,intr,exec 0 0

#Downloads
10.1.1.7:/mnt/HMS-Storage/Downloads /home/ben/Downloads nfs rw,hard,intr,exec 0 0

#Music
10.1.1.7:/mnt/HMS-Storage/Music /home/ben/Music nfs rw,hard,intr,exec 0 0

#Videos
10.1.1.7:/mnt/HMS-Storage/Videos /home/ben/Videos nfs rw,hard,intr,exec 0 0

#Pictures
10.1.1.7:/mnt/HMS-Storage/Pictures /home/ben/Pictures nfs rw,hard,intr,exec 0 0

#Movies
10.1.1.7:/mnt/HMS-Storage/Movies /home/ben/Movies nfs rw,hard,intr,exec 0 0

#Virtual Machine Storage
10.1.1.7:/mnt/HMS-Storage/VM-Storage /home/ben/VirtualBox-VMs nfs rw,hard,intr,exec 0 0

#Software
10.1.1.7:/mnt/HMS-Storage/Software /home/ben/Software nfs rw,hard,intr,exec 0 0

#Sessions
10.1.1.7:/mnt/HMS-Storage/Sessions /home/ben/Sessions nfs rw,hard,intr,exec 0 0

#FL-Studio-Projects
10.1.1.7:/mnt/HMS-Storage/FL-Studio-Projects /home/ben/FL-Studio-Projects nfs rw,hard,intr,exec 0 0

#FL-Studio-Data
10.1.1.7:/mnt/HMS-Storage/FL-Studio-Data /home/ben/FL-Studio-Data nfs rw,hard,intr,exec 0 0

#Active-Projects
10.1.1.7:/mnt/HMS-Storage/Active-Projects /home/ben/Active-Projects nfs rw,hard,intr,exec 0 0

#William-Cooper
10.1.1.7:/mnt/HMS-Storage/William-Cooper /home/ben/William-Cooper nfs rw,hard,intr,exec 0 0
```

---

### Post by arrrghhh on 2012-04-04
This is not an Ubuntu Server issue.  It's an Ubuntu Desktop / Gnome issue.

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

