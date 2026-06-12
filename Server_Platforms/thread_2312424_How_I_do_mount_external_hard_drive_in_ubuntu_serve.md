---
title: "How I do mount external hard drive in ubuntu server?"
date: 2016-02-04
forum: Server Platforms
---

### Post by gytis3 on 2016-02-04
Hi everybody,
I use ubuntu for my laptops, however now i have installed ubuntu server with samba file share for first time. For installing first time server i used an video from there [https://www.youtube.com/watch?v=ndAYZ0DJ-U4](https://www.youtube.com/watch?v=ndAYZ0DJ-U4) . Everything went good with my old PC and now i need to connect/mount my external hard drive for server. Hard drive which i need to add is 1TB space and that drive has important files which uses half space. This hard drive is in nfts format. So I need help to add this driver to server step by step if possible. My server is Ubuntu server 14.04.3 LTS.
With regards
Gytis.

---

### Post by howefield on 2016-02-04
You'll probably have better luck here.

Thread moved to the "*Server Platforms*" forum.

---

### Post by bab1 on 2016-02-04
> **gytis3 said:**
> Hi everybody,
I use ubuntu for my laptops, however now i have installed ubuntu server with samba file share for first time. For installing first time server i used an video from there [https://www.youtube.com/watch?v=ndAYZ0DJ-U4](https://www.youtube.com/watch?v=ndAYZ0DJ-U4) . Everything went good with my old PC and now i need to connect/mount my external hard drive for server. Hard drive which i need to add is 1TB space and that drive has important files which uses half space. This hard drive is in nfts format. So I need help to add this driver to server step by step if possible. My server is Ubuntu server 14.04.3 LTS.
With regards
Gytis.
Where in the Ubuntu file system do you want to mount this partition?  I have a 1TB partition that I mount at /srv/nas.  How many users are going to have access to the data on the mounted partition?  Will they need to access the same data?  If you are going to use this HDD in this manner on a permanent basis you should seriously think about moving the data off the disk and reformatting it to ext4.  Do you have all this data backed up to a separate location?

---

