---
title: "Dosemu+Foxpro 2.6"
date: 2009-08-03
forum: Virtualisation
---

### Post by yhudi on 2009-08-03
Hello all,

I have database foxpro 2.6 in windows 2003 server. I want my ubuntu client connect to windows server and run foxpro. I have install dosemu, and already mount the foxpro directory at server 2003. i have edit fstab:

#//192.168.20.1/application /mnt/foxpro cifs exec,credentials=/etc/cifspw 0 0 


#//192.168.20.1/application is my windows 2003 server. and
 /mnt/foxpro is my ubuntu directory.

at dosemu i have using lredir to mount  /mnt/foxpro as x with this syntax

lredir x: linux\fs/mnt/foxpro

at dosemu...when i change to drive x, all database is listed, but when run foxpro.exe, the error message is " the file is not exist." 

* if foxpro copy to local ubuntu, running well.
anybody can help me...thanks very much.

---

