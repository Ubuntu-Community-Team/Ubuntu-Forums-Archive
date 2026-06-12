---
title: "Folder Lock"
date: 2014-01-08
forum: Security
---

### Post by vushan108 on 2014-01-08
Hi,

Does anyone know how to create a folder lock in ubuntu 13.10??  
I don't want to encrypt or compress the files.  
Just a folder which needs a password to be accessed.

---

### Post by tfrue on 2014-01-09
I'm not sure about password protecting files, but you can set permissions in linux that will deny people from accessing files.

---

### Post by tfrue on 2014-01-09
If you are the owner of the file, say /home/vushan/Desktop/secret-file.txt, you can change the permission as defined by issuing the command ```
ls -ll /home/vushan/Desktop/
```
To set the permissions, use *chmod* so type:```
chmod 700 /home/vushan/Desktop/secret-file.txt
```
This will give only the owner read, write, execute (rwx) permissions over that file.

---

