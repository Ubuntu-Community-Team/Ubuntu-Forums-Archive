---
title: "Problem With GRUB Loader"
date: 2009-11-17
forum: Ubuntu One (CLOSED)
---

### Post by Keyazzie on 2009-11-17
Help!!!!
 
I am running Windows Vista Home Premium SP1 and I got this error after I deleted the partition for UBUNTU.  Is there any way to correct this error?
 
GRUB Loading:
Error: No Such Partition:
Grub Rescue>

---

### Post by Nostoc on 2009-11-17
> **Keyazzie said:**
> Help!!!!
 
I am running Windows Vista Home Premium SP1 and I got this error after I deleted the partition for UBUNTU.  Is there any way to correct this error?
 
GRUB Loading:
Error: No Such Partition:
Grub Rescue>

Grub is located on your Ubuntu partition, since you deleted that partition, it will not work.

You will have to restore the windows bootloader, wich can be done with the windows recovery console if you have the Vista install disc, or with the ubuntu LiveCD.


You will want to read this :  (the second part of the first post applies to you)
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

