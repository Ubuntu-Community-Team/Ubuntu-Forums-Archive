---
title: "Access to mount denied? Need some help."
date: 2008-09-08
forum: Server Platforms
---

### Post by mfreeman73 on 2008-09-08
I have an ubuntu server in my house to share files and I have samba setup on the server with security set to "share." I can access the share folder fine in windows, but I'd like to access it from my linux desktop (using Ubuntu 8.04).

I did this command to mount:
sudo mount -t smbfs //192.168.1.101/share /mnt/share

When I browse to the /mnt/share folder I can see my files, although their icons have an "X" on them. When I go to open one of them I get the error message: "Access to /mnt/share/file was denied."

Any reason for this? My shares don't have passwords on them and I don't have the security level on samba set to user security, but rather share. Anyone have any ideas?

---

### Post by Iowan on 2008-09-08
[http://ubuntuforums.org/showthread.php?t=914077]("http://ubuntuforums.org/showthread.php?t=914077")

By the way...
From the Ubuntu Forums Code of Conduct Section 1, Item 10:
> Please do not cross post, or post the same thing in multiple locations.

---

