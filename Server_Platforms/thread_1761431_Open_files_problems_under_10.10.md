---
title: "Open files problems under 10.10"
date: 2011-05-18
forum: Server Platforms
---

### Post by erezk on 2011-05-18
I am new to ubuntu.
I have opened a new file server which is serves a windows computers/files.
 
1. I found that from time to time especially if file is opend for long time, other can also access the file without any notification.
 
2. if someone else is accessing the file the fist one cannot access it anymore.
 
3. users cannot change the read only bit.
 
I suspect that the fstab is the problem. I add the relevant line below.
 
# /data was on /dev/cciss/c0d1p1 during installation
UUID=2DFD83F9112F93E3 /data ntfs rw,umask=000,gid=46 0 1
 
Need help ASAP, otherwise my boss will force me to install windows 2008 server.....

---

