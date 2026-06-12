---
title: "ole16 error when running configure."
date: 2010-03-15
forum: Wine
---

### Post by stfnmchr on 2010-03-15
Hi, I hope I won't be a nuisance but I want to compile wine from sources ([http://nickyt.org/?p=10](http://nickyt.org/?p=10) is the reason for this if you want to know) and when I run configure I get the error:
```

In file included from ole16.c:45:
compobj_private.h:37:18: error: dcom.h: No such file or directory
In file included from ole16.c:45:
compobj_private.h:78: error: expected specifier-qualifier-list before ‘IPID’
compobj_private.h:96: error: expected specifier-qualifier-list before ‘OID’
compobj_private.h:116: error: expected specifier-qualifier-list before ‘STDOBJREF’
compobj_private.h:131: error: expected specifier-qualifier-list before ‘OXID’
compobj_private.h:151: error: expected specifier-qualifier-list before ‘OXID’
In file included from ole16.c:45:
compobj_private.h:209: error: expected declaration specifiers or ‘...’ before ‘OID’
compobj_private.h:211: warning: type defaults to ‘int’ in declaration of ‘IPID’
compobj_private.h:211: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
compobj_private.h:212: warning: type defaults to ‘int’ in declaration of ‘IPID’
compobj_private.h:212: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
compobj_private.h:213: warning: type defaults to ‘int’ in declaration of ‘IPID’
compobj_private.h:213: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
compobj_private.h:214: warning: type defaults to ‘int’ in declaration of ‘IPID’
compobj_private.h:214: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
compobj_private.h:215: warning: type defaults to ‘int’ in declaration of ‘IPID’
compobj_private.h:215: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
compobj_private.h:218: error: expected declaration specifiers or ‘...’ before ‘STDOBJREF’
compobj_private.h:225: warning: type defaults to ‘int’ in declaration of ‘OXID’
compobj_private.h:225: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
compobj_private.h:238: error: expected ‘)’ before ‘oxid’
compobj_private.h:251: error: expected ‘)’ before ‘oxid’
compobj_private.h:257: error: expected declaration specifiers or ‘...’ before ‘OXID’
compobj_private.h: In function ‘apartment_getoxid’:
compobj_private.h:259: error: ‘oxid’ undeclared (first use in this function)
compobj_private.h:259: error: (Each undeclared identifier is reported only once
compobj_private.h:259: error: for each function it appears in.)
compobj_private.h:259: error: ‘const struct apartment’ has no member named ‘oxid’
make[2]: *** [ole16.o] Error 1
make[2]: Leaving directory `/home/stefan/Downloads/wine-1.0.1/dlls/ole32'
make[1]: *** [ole32] Error 2
make[1]: Leaving directory `/home/stefan/Downloads/wine-1.0.1/dlls'
make: *** [dlls] Error 2

```
Of course I tried googling, but pasting this into the search engine only gave me links to some 404's on a Russian forum :(

Wine 1.0.1, downloaded today from winehq, Ubuntu 9.10 Karmic Koala running on HP Compaq 6730s.

---

### Post by asdfoo on 2010-03-15
You should follow the AppDB for advice, not random blogs.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)

---

