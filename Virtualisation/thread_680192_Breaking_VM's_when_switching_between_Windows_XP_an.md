---
title: "Breaking VM's when switching between Windows XP and Ubuntu"
date: 2008-01-27
forum: Virtualisation
---

### Post by mwacky on 2008-01-27
On a dual boot setup, I've been using VMware Server to build vm's on Windows XP, then using VMware Player to play them from the same location when in Ubuntu, saves space, but sometimes the machine will not open, with a 'failed to lock file error'.  Anyone experience the same or similar problem on a dual boot setup?

---

### Post by Hmarroqu on 2008-02-03
Try virtualbox....

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

---

### Post by noogen on 2008-02-03
Is your file system ntfs?  If so, I think vmware in ubuntu is not expecting the file to be on ntfs but ext3.  Because it is a linux vmware, it probably try to lock file using linux command instead of ntfs and failed.

---

### Post by mwacky on 2008-02-05
> **noogen said:**
> Is your file system ntfs?  If so, I think vmware in ubuntu is not expecting the file to be on ntfs but ext3.  Because it is a linux vmware, it probably try to lock file using linux command instead of ntfs and failed.

Any fix for this?

---

