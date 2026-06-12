---
title: "pureftpd problem"
date: 2011-11-30
forum: Server Platforms
---

### Post by yavuz.maslak on 2011-11-30
I use pureftpd with mysql on ubuntu11.10 server. it works.

I have a directory whose has many files over 10000 files and several directories.
when i connect via ftp I can't see a directory in the directory.
But I can do cd that nested directory and see files in it.
it's directory has 777 as chmod.

Also I can't see uploaded new files in the directory via ftp. whereas I can see uploaded files via ssh. 

How can I solve that problem ?

---

### Post by yavuz.maslak on 2011-11-30
I solved my problem guys

I touched a file called LimitRecursion
I specified an enough value 50000 500 into it.
I restarted pureftpd 
I can see all directories and files anymore.

---

