---
title: "NFS mount at startup"
date: 2005-11-13
forum: Server Platforms
---

### Post by caspar_wrede on 2005-11-13
Hi

 my nfs server is not mounted automatically when I boot my laptop. It works when i enter ```
mount -a
``` after the machine has come up. 

Here is the appropriate line from my fstab
```
kronos:/        /mnt/kronos     nfs     rw              0       0
```

I suspect the ethernet card is not coming up before nfs shares are mounted. What to do?

Caspar

---

### Post by Juzz on 2005-11-14
This is of the top of my head at work, but you need to add the option that tells the mounter that networking is needed when trying to mount it:

_network
or
_networking

That at least works with my samba share on my server at home.

---

### Post by khaledagha on 2005-11-15
is the command 
mount -t nfs kronos:/    /mnt/kronos

working

---

