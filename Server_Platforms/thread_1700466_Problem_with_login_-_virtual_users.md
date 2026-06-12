---
title: "Problem with login - virtual users"
date: 2011-03-05
forum: Server Platforms
---

### Post by alfamuzjak on 2011-03-05
Hi,
Im running ubuntu server 10.10 on virtual mashine.
I installed and configured vsftpd with anonymous options and all worked fine (upload and download ok), but it failed when i try to disable anonymous and configure virtual users.

I completly follow both [vsftpd guide]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.3.0/EXAMPLE/VIRTUAL_USERS/README") and [one post in this forum which also worked -for him]("http://ubuntuforums.org/showthread.php?t=518293&highlight=virtual+users").

Except, insted db_load and db3_load i use db4.8_load - T -t hash...for creating db file. 

when i connect to my ftp server and login with those virtual usernames and passd's i get this:
```
530 Login incorrect.
Login failed.
```

Please help me, i dont know why this dont work for me!

---

### Post by alfamuzjak on 2011-03-05
I solved it, problem was with some pam modules

---

### Post by danieldamm on 2011-06-18
I encountered a similar problem, when using the guide: 
[http://ubuntuforums.org/showthread.php?t=518293&highlight=virtual+users](http://ubuntuforums.org/showthread.php?t=518293&highlight=virtual+users)
on a 10.04 server.

The problems seems to be an incorrect path to pam_userdb.so in /etc/pam.d/ftp

 /lib/i386-linux-gnu/security/pam_userdb.so worked for me.

---

