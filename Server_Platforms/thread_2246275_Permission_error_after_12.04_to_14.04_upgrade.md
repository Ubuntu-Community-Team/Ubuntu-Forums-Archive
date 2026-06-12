---
title: "Permission error after 12.04 to 14.04 upgrade"
date: 2014-09-29
forum: Server Platforms
---

### Post by eddie19 on 2014-09-29
**[SIZE=2][FONT=arial]Hello[/FONT][/SIZE]**

I just upgraded to 14.04 LTS from 12.04 LTS. I host multiple websites using Virtualmin and Webmin. I get a 403 error "Forbidden, you don't have permission to access / on this server." Virtualmin places the websites in the home folder.
     I have no clue as to what I need to change or how. Can anybody point me in the right direction? 

Thanks 
eddie19

---

### Post by irv on 2014-09-29
To check the permission at the command line type:
```
cd /var/
```
Then type:
```
ls -l
```
You should see something like this.
> total 52
drwxr-xr-x  2 root   root     4096 Sep 20 06:27 backups
drwxr-xr-x 13 root   root     4096 Sep 16 20:59 cache
drwxr-xr-x  2 vsftpd nogroup  4096 Sep 19 12:13 clients
drwxrwxrwt  2 root   root     4096 Sep 15 09:22 crash
drwxr-xr-x 44 root   root     4096 Sep 16 06:36 lib
drwxrwsr-x  2 root   staff    4096 Apr 10 17:11 local
lrwxrwxrwx  1 root   root        9 Sep 15 09:08 lock -> /run/lock
drwxrwxr-x 12 root   syslog   4096 Sep 29 08:55 log
drwxrwsr-x  2 root   mail     4096 Jul 22 17:48 mail
drwxr-xr-x  2 root   root     4096 Jul 22 17:48 opt
lrwxrwxrwx  1 root   root        4 Sep 15 09:08 run -> /run
drwxr-xr-x  5 root   root     4096 Sep 19 05:47 spool
drwxrwxrwt  2 root   root     4096 Sep 16 21:35 tmp
drwx------  3 root   bin      4096 Sep 29 08:54 webmin
drwxr-xr-x 38 irv    www-data 4096 Sep 17 07:59 www

Look at the permission of the www directory. This should tell you if it is set right. Also check the owner and who has rights to that directory. This is a good place to start.

---

### Post by irv on 2014-09-29
These are the three command for changing Permission and owner and group access.
```
 chgrp    Change group ownership
  chmod    Change access permissions
  chown Change file owner and group 
```

To use these commands check out this websit.
[http://ss64.com/bash/]("http://ss64.com/bash/")

---

