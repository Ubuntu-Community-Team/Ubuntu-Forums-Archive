---
title: "Unable to customize Ubuntu 13.04 (Beta-2)"
date: 2013-04-24
forum: Ubuntu Development Version
---

### Post by Suryabhan Singh on 2013-04-24
Hello,

I am trying to customize ubuntu 13.04  server by integrating someextra packages but I am always getting this error "No installable kernelwas found in the defined APT sources" or  base-installer: info: Foundkernels ' ' (Alt +f4). When through preseed I tried to skip this stage I gotanother error "an attempt to configure apt to install additional packagesfrom the cd failed" (Alt +f4). Please let me know how I will sort out thisissue.

Note: I also tried the same thing in ubuntu 12.10 (64 bit) and Ifaced the same issue in too.

Thanks
Suryabhan

---

### Post by dino99 on 2013-04-24
from /etc/apt/sources.list, comment out the line about "cd" and then update again. The system need indeed to search into the ubuntu archives (online) and not on the cd where it cant find something new of course.

---

### Post by Suryabhan Singh on 2013-04-24
How it is possible in Customized  ISO? Actually I customized Ubuntu  13.04/ Ubuntu 12.10 ISOs  and through these ISOs I am installing different machine, while installing I am getting these errors. I made lots of changes in "preseed"  file but I am not able to figure it out...


Thanks 
Suryabhan

---

### Post by dino99 on 2013-04-24
Have you followed that howto : [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)  ?

how those isos have been made ? using remastersys or uck ?

---

### Post by Suryabhan Singh on 2013-04-24
I followed the below link:

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

