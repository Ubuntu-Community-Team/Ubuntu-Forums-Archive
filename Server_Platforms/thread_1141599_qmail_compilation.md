---
title: "qmail compilation"
date: 2009-04-28
forum: Server Platforms
---

### Post by mazid on 2009-04-28
hello i was compiling qmail and get this error 

```
root@admin:/usr/local/src/qmail-1.03# make setup check
./load auto-str substdio.a error.a str.a 
/usr/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss mismatches non-TLS reference in substdio.a(substdo.o)
/lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [auto-str] Error 1
```any help ?

---

