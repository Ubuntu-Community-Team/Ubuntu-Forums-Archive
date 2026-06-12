---
title: "how to change default MPM module"
date: 2010-05-30
forum: Server Platforms
---

### Post by gyre007 on 2010-05-30
Hi I've been googling around looking for some hints about how to change default apache2 MPM module.
I know that apache2 comes precompiled with some default one - for unix machines it's mpm_prefork
I'm sure about that cos when I ran apache2 -l it return the following:

Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
**  prefork.c**
  http_core.c
  mod_so.c

but then again these are compiled into the binary....but are shipped with apache2 on ubuntu by default apparently...
Now I can see different IfModoule directives in apache.conf - each for different mpm but I simply CAN'T FIND a solution how to switch from one mpm to another...

I've been looking around on the acutal OS and found out following..
gyre@gyre-laptop:/etc/apache2$ ll /usr/sbin/apache2
lrwxrwxrwx 1 root root 34 2010-05-14 03:06 /usr/sbin/apache2 -> ../lib/apache2/mpm-prefork/apache2

so apache2 is actually a link to the mpm-prefork binary... ? am I right ?
I checked the content of /usr/lib/apache2/ directory and found out;

gyre@gyre-laptop:/etc/apache2$ ll /usr/lib/apache2/
total 28
drwxr-xr-x 2 root root 12288 2010-05-23 01:48 modules
drwxr-xr-x 2 root root  4096 2010-05-14 03:06 mpm-event
drwxr-xr-x 2 root root  4096 2010-05-14 03:06 mpm-itk
drwxr-xr-x 2 root root  4096 2010-05-14 03:06 mpm-prefork
drwxr-xr-x 2 root root  4096 2010-05-14 03:06 mpm-worker

each of mpm* subdirectories actually contains different apache2 binary:

gyre@gyre-laptop:/etc/apache2$ ll /usr/lib/apache2/mpm-*
/usr/lib/apache2/mpm-event:
total 1224
-rwxr-xr-x 1 root root 1248547 2010-04-13 20:31 apache2

/usr/lib/apache2/mpm-itk:
total 1204
-rwxr-xr-x 1 root root 1226720 2010-04-13 20:31 apache2

/usr/lib/apache2/mpm-prefork:
total 1196
-rwxr-xr-x 1 root root 1217974 2010-04-13 20:31 apache2

/usr/lib/apache2/mpm-worker:
total 1220
-rwxr-xr-x 1 root root 1244033 2010-04-13 20:31 apache2

I'm **GUESSING** with the different MPM module compiled in ?? am I right ?

Soo..am I correct that if I want to change the mpm the only thing I need to do is to change the symlink from the current default one which is pointing to mpm-prefork binary to the new by me picked mpm module and then restart apache2 ??

Thanks a lot for all the comments.
gyre

---

