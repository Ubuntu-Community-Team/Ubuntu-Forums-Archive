---
title: "Recovering from a boneheaded move - - -"
date: 2008-02-13
forum: Security Discussions
---

### Post by SoggyCornflake on 2008-02-13
Can somebody point me to a link where I can find the default permissions for all the files in the /var directory?

I was attempting to change the permissions for the /var/www directory, but in a moment of fat fingered forgetfullness, I did the command on the /var/ directory  (and all the subdirectorys.)  

Yes this sounds like something out of a chapter in the [Unix Hater's Handbook]("http://www.simson.net/ref/ugh.pdf"),

Can anybody point me to a guide as to what the default permissions are for Ubuntu? 

Thanks in advance.

---

### Post by p_quarles on 2008-02-14
Here's the output of ls -l /var on my machine, on which the perms haven't been touched:
```
drwxr-xr-x  2 root root  4096 2008-02-01 03:36 backups/
drwxr-xr-x 12 root root  4096 2008-02-02 23:46 cache/
drwxr-xr-x  2 root root  4096 2008-02-01 09:50 games/
drwxr-xr-x 46 root root  4096 2008-02-10 15:30 lib/
drwxrwsr-x  2 root staff 4096 2007-11-19 12:21 local/
drwxrwxrwt  2 root root  4096 2008-02-13 22:13 lock/
drwxr-xr-x 10 root root  4096 2008-02-13 22:13 log/
drwxrwsr-x  2 root mail  4096 2008-02-01 03:36 mail/
drwxr-xr-x  2 root root  4096 2008-02-01 03:36 opt/
drwxr-xr-x 17 root root  4096 2008-02-13 23:06 run/
drwxr-xr-x  6 root root  4096 2008-02-01 06:59 spool/
drwxrwxrwt  5 root root  4096 2008-02-13 23:49 tmp/
drwxr-xr-x  3 root root  4096 2008-02-01 06:22 www/
```

---

### Post by HermanAB on 2008-02-14
Screw-ups like this happens to everybody sooner or later, but it generally only happens once...

The easiest solution is to re-install.  It only takes about 30 minutes and if your /home is on a separate partition as it should be, then all you need to do is ensure that you don't format /home during the re-install.

Cheers,

Herman

---

