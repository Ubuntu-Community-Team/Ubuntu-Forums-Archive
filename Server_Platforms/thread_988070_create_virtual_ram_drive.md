---
title: "create virtual ram drive"
date: 2008-11-20
forum: Server Platforms
---

### Post by goksu on 2008-11-20
hello,

how do I create a virtual hdd drive on the ram under ubuntu and mount & umount saving the file to hdd before loosing any data?
preferably before complete power loss (running on laptop).

I have a database that does a lot of read write that will eat the disk very soon if I do not find a solution to it. it is also slow.

thank you.

---

### Post by Krupski on 2008-11-20
> **goksu said:**
> hello,

how do I create a virtual hdd drive on the ram under ubuntu and mount & umount saving the file to hdd before loosing any data?
preferably before complete power loss (running on laptop).

I have a database that does a lot of read write that will eat the disk very soon if I do not find a solution to it. it is also slow.

thank you.

"/dev/shm" is a pre-made ramdrive that initially uses no memory, but will grow up to 1/2 of your physical ram size as needed.

That is, if you have 4GB of ram installed, you can save up to 2 GB of data in /dev/shm.

Note that /dev/shm is a RAM drive and all data will be lost upon reboot. 

Hope this helps.

---

