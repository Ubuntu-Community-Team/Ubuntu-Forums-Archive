---
title: "problem installing SQLat..."
date: 2008-07-19
forum: Security
---

### Post by Mia_tech on 2008-07-19
I'm trying to install SQLat and it depends on freetds, which I installed before, but when running ./configure for sqlat I get this error
```
checking for tds_alloc_login in -ltds... no
configure: error: Unable to find freetds library
```

any help appreciated

thanks

---

### Post by Steveway on 2008-07-19
> **Mia_tech said:**
> I'm trying to install SQLat and it depends on freetds, which I installed before, but when running ./configure for sqlat I get this error
```
checking for tds_alloc_login in -ltds... no
configure: error: Unable to find freetds library
```

any help appreciated

thanks

You need the development files if you need it for compilation. So look for a version of it in synaptic that ends with -dev.

---

### Post by Mia_tech on 2008-07-20
that is besides the build-essential package?... I did a search in synaptic and there are lots of files ending in -dev, could you be more specific?


thanks

---

### Post by Mia_tech on 2008-07-20
my bad I should have assume that you were talking about freetds...I found them

---

### Post by Mia_tech on 2008-07-20
I'm still getting errors when compiling SQLat duing make
```
sqllib.c: In function ‘value_as_string’:
sqllib.c:695: error: ‘TDSBLOBINFO’ undeclared (first use in this function)
sqllib.c:695: error: (Each undeclared identifier is reported only once
sqllib.c:695: error: for each function it appears in.)
sqllib.c:695: error: expected expression before ‘)’ token
sqllib.c:706: warning: ignoring return value of ‘realloc’, declared with attribute warn_unused_result
sqllib.c:727: warning: ignoring return value of ‘realloc’, declared with attribute warn_unused_result
sqllib.c:736: warning: ignoring return value of ‘realloc’, declared with attribute warn_unused_result
make: *** [sqllib.o] Error 1

```

thanks

---

### Post by Mia_tech on 2008-07-21
this might be of help to anyone.. at the end of the "make install" for the freetds app I get this message....to it seems that it installed
```
/bin/bash ./mkinstalldirs /usr/local/etc
if test ! -f /usr/local/etc/freetds.conf; then \
		/usr/bin/install -c -m 644 ./freetds.conf /usr/local/etc/freetds.conf; \
	fi
if test ! -f /usr/local/etc/locales.conf; then \
		/usr/bin/install -c -m 644 ./locales.conf /usr/local/etc/locales.conf; \
	fi
make[2]: Leaving directory `/home/jorge/freetds-0.82'
make[1]: Leaving directory `/home/jorge/freetds-0.82'

```
any help appreciated

thanks

---

### Post by Mia_tech on 2008-07-21
and I get this when running "sudo make" for sqlat
```
 sudo make
gcc -O6 -Wall -DNDEBUG=0 -Iinclude -g -O2   -c -o sqllib.o sqllib.c
In file included from sqllib.c:22:
include/sqllib.h:73: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sqllib.c: In function ‘value_as_string’:
sqllib.c:695: error: ‘TDSBLOBINFO’ undeclared (first use in this function)
sqllib.c:695: error: (Each undeclared identifier is reported only once
sqllib.c:695: error: for each function it appears in.)
sqllib.c:695: error: expected expression before ‘)’ token
sqllib.c:706: warning: ignoring return value of ‘realloc’, declared with attribute warn_unused_result
sqllib.c:727: warning: ignoring return value of ‘realloc’, declared with attribute warn_unused_result
sqllib.c:736: warning: ignoring return value of ‘realloc’, declared with attribute warn_unused_result
make: *** [sqllib.o] Error 1

```

thanks

---

