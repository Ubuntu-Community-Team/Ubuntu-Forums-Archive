---
title: "Require password for file/folder delete?"
date: 2016-07-14
forum: Security
---

### Post by robphelan on 2016-07-14
Hey everyone.. running 14.04 on my NAS. 

I'd like to require a password to be entered in order to delete a folder of any file within. These are all my media files.. nothing that I want to restrict access to other than for deletions.

Is there any good way to enforce this?

thanks,
rp

---

### Post by ajgreeny on 2016-07-14
You could try adding the immutable flag to the files in the folder by running command ```
sudo chattr +i /path/to/folder/*
``` which will allow the files to be read but not deleted or edited in any way.  

It assumes that chattr will allow the wildcard of * to be used for all the files in that folder, which I believe it will, and also that the NAS is formatted to filesystem which accepts Linux permissions; it will not work if the NAS is formatted to a typical MS filesystem of NTFS or FAT32.

---

