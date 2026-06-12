---
title: "U-boot complie problem"
date: 2012-08-03
forum: Server Platforms
---

### Post by nikibg on 2012-08-03
When i try to compile u-boot its returns me 

```
for dir in tools examples api_examples ; do make -C $dir _depend ; done
make[1]: Entering directory `/home/niki/eldk/usr/src/u-boot-1.3.2/tools'
make[1]: Nothing to be done for `_depend'.
make[1]: Leaving directory `/home/niki/eldk/usr/src/u-boot-1.3.2/tools'
make[1]: Entering directory `/home/niki/eldk/usr/src/u-boot-1.3.2/examples'
make[1]: Nothing to be done for `_depend'.
make[1]: Leaving directory `/home/niki/eldk/usr/src/u-boot-1.3.2/examples'
make[1]: Entering directory `/home/niki/eldk/usr/src/u-boot-1.3.2/api_examples'
make[1]: Nothing to be done for `_depend'.
make[1]: Leaving directory `/home/niki/eldk/usr/src/u-boot-1.3.2/api_examples'
Generating include/autoconf.mk
cc1: error: unrecognized command line option "-march=armv5"
cc1: error: unknown ABI specified: 'apcs-gnu'
cc1: error: unrecognized command line option "-mabi=apcs-gnu"
make: *** [include/autoconf.mk] Error 1
```
what is wrong 
:confused:

---

