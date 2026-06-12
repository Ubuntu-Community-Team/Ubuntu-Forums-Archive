---
title: "failed to mount external hard disk"
date: 2010-09-09
forum: Server Platforms
---

### Post by ryan1219 on 2010-09-09
System: ubuntu server edition 10.10
Hardisk: a 160g usb external hard disk, formatted in win7 with NTFS format. 

%fdisk -l
returns:
Device Boot     .... System
/dev/sdg1            NPFS/NTFS


%sudo mount -t ntfs-3g /dev/sdg1 /media/external
returns:
fuse: failed to create temporary directory

Have anyone seen this before?

Thanks

---

### Post by gobbledigook on 2010-09-09
i don't have much of an idea i'm afraid... the /media/external dir does exist? :) you could try with some of the default options or to mount as read only:

```
sudo mount -t ntfs-3g -o defaults /dev/sdg1 /media/external

sudo mount -t ntfs-3g /dev/sdg1 -o ro /media/external
```

see the [mount man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mount+8") for more options

---

