---
title: "apache2 bw_mod"
date: 2005-12-14
forum: Server Platforms
---

### Post by mat3 on 2005-12-14
hi

I have got ubuntu 5.1 breezy and I've installed Xampp (apache2, php, mysql, all in one package)

Yesterday I tried to install another module for apache (i need limit the bandwidth) [http://www.ivn.cl/apache/#bandwidth](http://www.ivn.cl/apache/#bandwidth)

I tried to install it in hard way (look here [http://www.ivn.cl/apache/bw_mod-0.6.txt](http://www.ivn.cl/apache/bw_mod-0.6.txt)) becouse Xampp installed apache2 in different location.

when I tried to create .so file I saw something like this:


```
mate@ojjojojo:/media/hda5/mate/mod1$ sudo libtool --silent --mode=compile gcc -g -O2 -pthread -DLINUX=2 -D_REENTRANT -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -D_SVID_SOURCE -I/usr/include/apache2 -I/usr/include/apr-0 -Wall -g -prefer-pic -c bw_mod-0.5.c && touch bw_mod-0.5.slo
bw_mod-0.5.c: In function 'update_counters':
bw_mod-0.5.c:513: warning: pointer targets in passing argument 1 of 'apr_atomic_cas' differ in signedness
bw_mod-0.5.c:525: warning: pointer targets in passing argument 1 of 'apr_atomic_set' differ in signedness
bw_mod-0.5.c: In function 'bw_filter':
bw_mod-0.5.c:655: warning: pointer targets in passing argument 1 of 'apr_atomic_inc' differ in signedness
bw_mod-0.5.c:684: warning: pointer targets in passing argument 1 of 'apr_atomic_dec' differ in signedness
bw_mod-0.5.c:759: warning: pointer targets in passing argument 1 of 'apr_atomic_dec' differ in signedness
bw_mod-0.5.c:783: warning: pointer targets in passing argument 1 of 'apr_atomic_dec' differ in signedness
```

how to solve it? what is apr_atomic? Plz help.

---

### Post by mat3 on 2005-12-15
ok I solved it. I had to install devel for Xampp.

---

