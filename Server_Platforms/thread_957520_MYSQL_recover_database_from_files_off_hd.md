---
title: "MYSQL: recover database from files off hd?"
date: 2008-10-24
forum: Server Platforms
---

### Post by bronkeydain on 2008-10-24
Hello people,

My server 7.10 HD has become unbootable (long story). I am trying to fix this.

My main concern is getting my Mysql databases up and running again.
I can access the drive. Is it possible to recover the mysql databases by copying certain files to my new system? Any other way to recover mysql, or even better the whole lamp config?

Thanks in advance...

---

### Post by bronkeydain on 2008-10-25
No one?

I just wanted to know if I can restore my databases from my HD that is not booting anymore.
If I get it to boot I will do a mysqldump and all is good, but if I can't get it to boot, surely there must be a way to get my databases back?

---

### Post by bronkeydain on 2008-10-25
Right, it seems all you have to do is copy /var/lib/mysql/mydata/ to the new hd (stop mysql before doing so). Will try that now...

---

### Post by bronkeydain on 2008-10-25
I don't have /var/lib/mysql/mydata/. I have tried to copy /var/lib/mysql but now I get a bunch of error messages when starting Mysql. Will reinstall Mysql and look for another way of doing this.

---

### Post by bendog on 2010-05-24
did you have any luck?

---

