---
title: "ftp over tls Yes/No question"
date: 2007-07-08
forum: Server Platforms
---

### Post by Gagle on 2007-07-08
I've secured my proftpd (ftp...) server using the tls module. (By this I mean that I edited accordingly the proftpd.conf file....).
I want to know if it is necessary for the the tls module to be compiled-in proftpd ?
By this I mean that issuing the following command: 
```
 /usr/sbin/proftpd -l 
```
I get the list of compiled-in modules but the mod_tls.c file doesn't appear in the list.

If details are needed or my post doesn't make sense, feel free to ask for a comprehensible question.

regards,

Gagle

---

### Post by Gagle on 2007-07-13
Anyone ?

---

### Post by Mr. C. on 2007-07-13
It appears the module must be compiled, but not compiled into proftpd.  It is loaded dynamically at runtime, when requested.

The list of compiled in modules are those specifically compiled into the core proftpd program.

Hope this helps,
MrC

---

