---
title: "Ubuntu 12.04 not working in Virtual"
date: 2013-08-16
forum: Virtualisation
---

### Post by graphicsmanx1 on 2013-08-16
I recently installed Virtualbox on a new computer that is running Windows 7 but for the life of me I cannot figure out why my shared folder is not updating correctly.  

I have installed Guest Additions.  Went to /media/folder and the shared directory was working yesterday and updating but within 24 hours anything I add to the shared folder is not working.  In virtualbox I did setup Shared Folder and set it to Auto-Mount yes with full access.  Where am I going wrong?

If I recall when I ran under XP and virtual the media folder also created a folder in /mnt with ```
sudo mount -t vboxsf -o uid=1000,gid=1000 shared /mnt/folder
``` and it would work.  Now when I try that in Windows 7 I get an error: /sbin/mount.vboxsf: mounting failed with the error: Protocol error.  Any ideas?  I did make sure the folder was there in mnt and I created the folder with ```
sudo mkdir /mnt/folder
```.  Im stuck please educate me.   How can I get the folder in media to auto update?

If it does help I did send a shortcut to the desktop with ln -s /media/folder /home/name/Desktop/ but I dont see how that would have been the issue.

---

### Post by howefield on 2013-08-16
Thread moved to "*Virtualisation*" forum.

---

