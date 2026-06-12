---
title: "[WARNING] Missing mod_tls.c module in proftpd edgy package"
date: 2006-10-30
forum: Server Platforms
---

### Post by frodon on 2006-10-30
Just few words to let you know that the proftpd package provided in edgy eft hasn't been compiled with the mod_tls.c module.
Therefore you won't be able to enable TLS encryption with this package.

Even worse, if you were running a FTP server on dapper and updated to edgy you may not have noticed this because depending on how you put it in your proftpd.conf file it may not complain when starting the server.

I have filled a bug report, feel free to add comments : 
[https://launchpad.net/distros/ubuntu/+source/proftpd/+bug/68735](https://launchpad.net/distros/ubuntu/+source/proftpd/+bug/68735)

---

### Post by dannyboy79 on 2006-11-08
> **frodon said:**
> Just few words to let you know that the proftpd package provided in edgy eft hasn't been compiled with the mod_tls.c module.
Therefore you won't be able to enable TLS encryption with this package.

Even worse, if you were running a FTP server on dapper and updated to edgy you may not have noticed this because depending on how you put it in your proftpd.conf file it may not complain when starting the server.

I have filled a bug report, feel free to add comments : 
[https://launchpad.net/distros/ubuntu/+source/proftpd/+bug/68735](https://launchpad.net/distros/ubuntu/+source/proftpd/+bug/68735)
frodon, couldn't you have at least given me credit for this???

Also, you should have stated that this affects the version in Dapper as well!!!!

---

### Post by frodon on 2006-11-08
But this don't affect dapper.

---

### Post by dannyboy79 on 2006-11-08
> **frodon said:**
> But this don't affect dapper.

huh, i told you about this long time ago, if you do a sudo aptitude update and a sudo aptitude upgrade proftpd gets updated to version 1.3.0 which is what I have on dapper and it doesn't have mod_tls in it. I can't believe you don't remember me telling you this!!! i even posted the thread long before you posted this one, see it here! [http://ubuntuforums.org/showthread.php?t=286147&highlight=proftpd](http://ubuntuforums.org/showthread.php?t=286147&highlight=proftpd)

which was the whole reason you posted the bug, or at least that's what you told me in the pm you sent!

---

