---
title: "VLD installation error"
date: 2006-07-31
forum: Server Platforms
---

### Post by sford999 on 2006-07-31
I`m trying to install the Vulcan Logic Disassembler into apache/php5-dev/ mysql but I keep getting the following error

> sford999@sford999-desktop:/usr/lib/php5/vld$ make
/bin/sh /usr/lib/php5/vld/libtool --mode=compile gcc  -I. -I/usr/lib/php5/vld -D PHP_ATOM_INC -I/usr/lib/php5/vld/include -I/usr/lib/php5/vld/main -I/usr/lib/php 5/vld -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/u sr/include/php5/Zend -I/usr/include/php5/ext  -DHAVE_CONFIG_H  -g -O2   -c /usr/ lib/php5/vld/srm_oparray.c -o srm_oparray.lo
 gcc -I. -I/usr/lib/php5/vld -DPHP_ATOM_INC -I/usr/lib/php5/vld/include -I/usr/l ib/php5/vld/main -I/usr/lib/php5/vld -I/usr/include/php5 -I/usr/include/php5/mai n -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -DHA VE_CONFIG_H -g -O2 -c /usr/lib/php5/vld/srm_oparray.c  -fPIC -DPIC -o .libs/srm_ oparray.o
/usr/lib/php5/vld/srm_oparray.c: In function 'vld_get_special_flags':
[B]/usr/lib/php5/vld/srm_oparray.c:354: error: 'ZEND_JMP_NO_CTOR' undeclared (first  use in this function)
/usr/lib/php5/vld/srm_oparray.c:354: error: (Each undeclared identifier is repor ted only once
/usr/lib/php5/vld/srm_oparray.c:354: error: for each function it appears in.)
make: *** [srm_oparray.lo] Error 1[/B]


Any idea whats causing this?

---

