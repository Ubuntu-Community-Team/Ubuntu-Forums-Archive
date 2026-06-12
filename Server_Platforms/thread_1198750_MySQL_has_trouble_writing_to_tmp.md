---
title: "MySQL has trouble writing to /tmp"
date: 2009-06-27
forum: Server Platforms
---

### Post by fogster on 2009-06-27
I'm really confused here. MySQL is running fine, and I can insert data into rows and all that.

But if I try to do "meta" operations like showing a table structure, I get this error:
> 
mysql> show columns from cacti.data_template_rrd like 'name';
ERROR 1 (HY000): Can't create/write to file '/tmp/#sql_7ec_0.MYI' (Errcode: 13)


This is a pretty new Ubuntu 9.04 machine, with a fresh MySQL installation, so I'm perplexed. 
> 
# ls -ldh /tmp/
drwxr-xr-t 6 root root 4.0K Jun 27 21:15 /tmp/


I tried setting the sticky bit (the "t" on the end of the file permissions), but that was no help. (Yes, I restarted MySQL.) I haven't changed my.cnf at all, and tmpdir is, indeed, set to /tmp in my.cnf.

mysql.err and mysql.log are both 0 bytes. Has anyone seen this before? It's really aggravating me.

---

### Post by fogster on 2009-06-28
I ran an fsck on the partition, and it was clean. Now I'm really confused.

---

### Post by LinkinCable on 2009-06-29
Try to chmod the directory

[PHP]chmod 777 tmp[/PHP]

Im not sure if you need lower permissions but if it is the chmod then you will find out by trying it very high, just on the dir not all the files iv you need ir recursively try adding a -R between the command and the 777

---

