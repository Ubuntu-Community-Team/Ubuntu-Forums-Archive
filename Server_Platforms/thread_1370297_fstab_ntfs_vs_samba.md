---
title: "fstab ntfs vs samba"
date: 2010-01-02
forum: Server Platforms
---

### Post by ivago on 2010-01-02
Hi,

I have a dualboot with Karmic (x64) and widnows 7 (x64)
My data is stored on a ntfs partition (mnt/data) and shared with samba to my workgroup.
When I share my /tmp dir every can browse my workgroup and see my samba server. When I share /mnt/data nobody can browse my workgroup and see my samaba server.

How do I mount ntfs so that it is accessible to everyone (like guest samba users).Now I have 
```
/dev/sda7 /mnt/data       ntfs  defaults 0 0
 
```
When I share my /media/backup (a fat32 1TB usb drive) all data is shared perfectely over the network, so it's definetly a permissiosn problem, I need the +4GB file support of ntfs so formatting it to fat32 is not an option, also need it in windows 7 so ext4 etc is also not possible///

---

