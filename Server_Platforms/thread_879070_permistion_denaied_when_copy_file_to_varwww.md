---
title: "permistion denaied when copy file to /var/www"
date: 2008-08-03
forum: Server Platforms
---

### Post by masoud23 on 2008-08-03
Hi

Why do I get this message when I copy a file into a map under /var/www/ and run it  from localhost (with apache 2). 

Forbidden

You don't have permission to access /hemsida/examen.html on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80

It works well when i create new php or html file in the same map problem appears only when i copy files from some were else!! how do i fix this?

Tanks in advance

---

### Post by GreenN00b on 2008-08-03
You have to give others read access on the files you have copied there.
Right click on files from nautilus, select properties and on permissions tab make sure everybody has read access.

---

### Post by cpetercarter on 2008-08-03
/var/www is probably owned by root. You may need to use "sudo" to copy to it.

---

### Post by masoud23 on 2008-08-03
Tanks! It is working now!

---

