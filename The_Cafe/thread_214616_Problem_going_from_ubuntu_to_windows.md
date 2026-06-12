---
title: "Problem going from ubuntu to windows"
date: 2006-07-12
forum: The Cafe
---

### Post by DigitalDuality on 2006-07-12
d

---

### Post by siimo on 2006-07-12
log into the PC via linux or a live CD and as root change the permission of the folders you need or even everything if you want like: 

chmod 777 -R /mounted/partition

(this gives read, write and execute to EVERYONE on EVERY file but since you will be using them from windows it doesn't matter) 

or you could give readonly permission but not write and execute or only read and write 

read: man chmod, for details.

---

### Post by DigitalDuality on 2006-07-12
d

---

### Post by B0rsuk on 2006-07-13
This might be considered a dirty fix by some, but you can use explore2fs:

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

I really like it, it's a non-invasive way to get something from linux partition. (Invasive would be installing a driver on someone's machine, etc).

---

### Post by Reshin on 2006-07-13
> **B0rsuk said:**
> This might be considered a dirty fix by some, but you can use explore2fs:

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

I really like it, it's a non-invasive way to get something from linux partition. (Invasive would be installing a driver on someone's machine, etc).

I use it to0 'cuz I still don't trust linux's NTFS-drivers writing abilities enough. Downside is, it gives full read-rights to every dir on that partition. So much for privacy. Can't write with it, thought

---

