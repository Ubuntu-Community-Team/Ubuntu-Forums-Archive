---
title: "Confine vsftpd to specific directory?"
date: 2016-10-31
forum: Server Platforms
---

### Post by frank2222 on 2016-10-31
Very frustrated. Hoping you guys can help.
I've set up the default vsftpd config and I can connect to it but it shows my entire drive. 
I"ve tried to restrict it to a specific folder using this addition to the config file...

local_root=/home/frank/folder

But it still allows my user to go up directories?

Any help appreciated

Edited typo:

---

### Post by slickymaster on 2016-10-31
*Thread moved to **Server Platforms**.*

---

### Post by Speculos on 2016-10-31
Hi Franck !

Don't be frustrated vsftpd is a very good FTP server but a bit complicated for chroot users.

Have you try to chroot your user ? Do you use local or virtual users ?

Take a look at this variable

```
chroot_local_user=YES
```

Meanwhile can you post your config file !?

```
/etc/vsftpd.conf
```

---

### Post by dudumomo on 2016-11-01
Hi Franck,

I think this tutorial can help you depending on how you want to do it.
[http://unix.stackexchange.com/questions/94603/limit-ftp-access-only-to-the-var-www-with-vsftpd](http://unix.stackexchange.com/questions/94603/limit-ftp-access-only-to-the-var-www-with-vsftpd)

---

### Post by frank2222 on 2016-11-01
Thanx for the reply's guys. I got it to work by chmod and chroot + matching folder in config file.
Thanx again

---

