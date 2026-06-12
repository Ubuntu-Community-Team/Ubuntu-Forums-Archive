---
title: "How to get Samba to Inherit Ownership"
date: 2012-03-06
forum: Server Platforms
---

### Post by Thund3rstruck on 2012-03-06
Hi guys, 

Migrated from a FreeNAS BSD Based NAS to a Ubuntu Server based NAS by manually installing and configuring Samba. 

My trouble is that I need new directories and files created by users to inherit the parent directory owner. When Lisa creates a file on a Samba share I do not want the file to be owned by Lisa:Lisa, I want it to be owned by it's parent owner root:mgrphotos. 

I have tried setting inherit owner and inherit permissions in the global section of smb.conf but it apprantly does nothing because files and folders are still getting ownership from the user and not the parent. 


Cheers!
-T3

---

### Post by Thund3rstruck on 2012-03-06
```
chmod g+s /media/share/disk1/Photos
```

The sticky bit allows for what I want.

---

