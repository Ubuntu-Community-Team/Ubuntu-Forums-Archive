---
title: "migration to different size array"
date: 2016-05-11
forum: Server Platforms
---

### Post by cicibau on 2016-05-11
I have a a server with 2 hdd SATA (2x1 TB) in software array configured by Ubuntu 12.04 LTS.
Now I bought another server which has approximately the same hardware configuration except for the fact that it has 8 x 500 GB SAS HDD. I want to know if it is possible to migrate the first server to the second one - basically to migrate the Ubuntu installation to a different size array and use all the size of the second array...

---

### Post by howefield on 2016-05-11
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2016-05-11
First, be more specific, do you have raid1 mirror on the 2x1TB disks? Is it one big root partition or you have OS partition and data partition(s)?

On the new server, how do you plan to organize the disks? raid6? Will it also be mdadm software raid? Many branded server raid controllers do not play friendly with linux software raid, they want you to use their own raid.

But in general, yes, you can transfer over the whole OS and of course any unused extra space will be there to be used...

---

### Post by lukeiamyourfather on 2016-05-12
Given the age of the installation (and the fact that support will end less than a year from now for 12.04 LTS) I'd personally try to setup 16.04 LTS on the new server and setup applications manually while using the old server for reference on how things were setup.

---

