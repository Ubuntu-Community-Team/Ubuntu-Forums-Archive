---
title: "diskfilter error?"
date: 2014-05-29
forum: Server Platforms
---

### Post by putz30002 on 2014-05-29
I am in the process of setting up a simple SAMBA box with a software RAID 1 setup. I did the initial install, a non raid partition on each drive for SWAP and then the remaining space on each drive of equal size setup as RAID 1 and configured for OS install and boot. I installed 14.04 server and for the most part it appears to be working. However, every time it boots up I get the following error message "error: diskfilter writes are not supported. Press any key to continue..._". 

What does that mean and what can I do to eliminate the error message?

---

### Post by putz30002 on 2014-06-02
bump

---

### Post by agarrett5 on 2014-07-14
I'm having the same issue.  I have tried many things from looking at various other posts to no avail.  I have tried many things including replacing 'etc/grub.d/10_linux' with ''quick_boot="1"' with 'quick_boot="0"'' etc.

---

