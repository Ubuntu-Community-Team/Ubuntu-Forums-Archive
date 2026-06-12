---
title: "Can't connect to local MySQL server through Socket"
date: 2010-05-23
forum: Server Platforms
---

### Post by portiris on 2010-05-23
Hello I'm pretty new to Linux and this is my first post here.

Whenever I try to connect to MySQL, I get the following message:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

It worked just fine the other day, then are I ran some updates and setup port forwarding to this computer [Ubuntu Server 10.04 LTS].

Edits:
---------------------------
Forgot to say: I did look this up before and the common fix (for older distros) seemed to be to link to the file accidentally placed in the /tmp directory, but it isn't there.

whereis mysqld.sock

returns

mysqld: /usr/sbin/mysqld /usr/share/man/man8/mysqld.8.gz

which didn't seem right to me

---

### Post by portiris on 2010-05-23
Nevermind. I think that the last attempt at fixing it ([http://ubuntuforums.org/showthread.php?t=1484736](http://ubuntuforums.org/showthread.php?t=1484736)) finally worked when I rebooted.

---

