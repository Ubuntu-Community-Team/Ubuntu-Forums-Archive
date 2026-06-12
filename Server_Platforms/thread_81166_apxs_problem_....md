---
title: "apxs problem ..."
date: 2005-10-23
forum: Server Platforms
---

### Post by dbee on 2005-10-23
Hi,

I still can't compile in modules from apxs ... It's been quite a while since I've started to try to do this (almost two weeks and  counting). 

If anyone knows the problem I'd be mighty obliged 

root@ubuntu:/usr/local/apache2/bin # ./apxs -cia mod_security.c
/usr/local/apache2/build/libtool --silent --mode=compile gcc -prefer-pic  -DAP_HAVE_DESIGNATED_INITIALIZER -DLINUX=2 -D_REENTRANT -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -D_SVID_SOURCE -D_GNU_SOURCE -g -O2 -pthread -I/usr/local/apache2/include  -I/usr/local/apache2/include   -I/usr/local/apache2/include   -c -o mod_security.lo mod_security.c && touch mod_security.slo
gcc: mod_security.c: No such file or directory
gcc: no input files
apxs:Error: Command failed with rc=65536
.

I've moved mod_security.c into

/usr/local/apache2/modules

but it still says that it's not there ...  :confused: 

Does anyone have experience troublesooting apxs ??

---

### Post by dbee on 2005-10-23
Simple directory problem .... d'oh :rolleyes:

---

