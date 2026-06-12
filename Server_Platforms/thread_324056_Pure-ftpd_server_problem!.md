---
title: "Pure-ftpd server problem!"
date: 2006-12-23
forum: Server Platforms
---

### Post by pzhukke on 2006-12-23
Hi!

Yesterday I installed Pure-FTPD server with MySQL Auth as the guide on [http://download.pureftpd.org/pub/pure-ftpd/doc/README.MySQL]("http://download.pureftpd.org/pub/pure-ftpd/doc/README.MySQL") says, and it almost works fine, exept this:

When I login to any user with a ftp program, I can click on the "Up one page" -button, and I can goto any directory I want ](*,) 

And WTH is this for kinda problem??:-k 

Probebly it's some setting somewhere who tells the server to bind the user to a specific directory, but I donno, thats why I posted this Thread:cool: 

So does any1 know how to fix this, please post!

---

### Post by fmasi on 2007-09-20
Have you verify if you have chroot on?
if you have a file caled ChrootEveryone whith yes on it you will be bloking users to ther home directory.

```
root@suzi:/etc/pure-ftpd/conf# cat ChrootEveryone 
Yes
root@suzi:/etc/pure-ftpd/conf#
```

if that is your case just delete the file or change it to No

---

