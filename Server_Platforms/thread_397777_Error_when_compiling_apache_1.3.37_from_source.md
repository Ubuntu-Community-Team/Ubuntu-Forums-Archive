---
title: "Error when compiling apache 1.3.37 from source"
date: 2007-03-31
forum: Server Platforms
---

### Post by PopcornEaterMan on 2007-03-31
I am following the instructions on [http://www.howtoforge.com/howto_apache_mod_ssl_php](http://www.howtoforge.com/howto_apache_mod_ssl_php)
and I have reached step 3, where you compile and install apache.  I have downloaded apache 1.3.37 because I want something stable and mature. 

anyhow, after executing "make" I get a compile error.  

Can someone tell me how I can resolve this problem?

from the terminal:
=============================================
elow@ubuntu:/tmp/apache_1.3.37$ sudo make
Password:
===> src
make[1]: Entering directory `/tmp/apache_1.3.37'
make[2]: Entering directory `/tmp/apache_1.3.37/src'
===> src/regex
make[3]: Nothing to be done for `all'.
<=== src/regex
===> src/os/unix
make[3]: Nothing to be done for `all'.
<=== src/os/unix
===> src/ap
make[3]: Nothing to be done for `all'.
<=== src/ap
===> src/main
make[3]: Nothing to be done for `all'.
<=== src/main
===> src/lib
===> src/lib/expat-lite
make[4]: Nothing to be done for `all'.
<=== src/lib/expat-lite
<=== src/lib
===> src/modules
===> src/modules/standard
gcc -c  -I../../os/unix -I../../include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DNO_DBM_REWRITEMAP -DMOD_SSL=208128 -DUSE_HSREGEX -DEAPI -DUSE_EXPAT -I../../lib/expat-lite `../../apaci` -fpic -DSHARED_MODULE mod_auth_dbm.c && mv mod_auth_dbm.o mod_auth_dbm.lo
mod_auth_dbm.c:42:18: error: ndbm.h: No such file or directory
mod_auth_dbm.c: In function ‘get_dbm_pw’:
mod_auth_dbm.c:110: error: ‘DBM’ undeclared (first use in this function)
mod_auth_dbm.c:110: error: (Each undeclared identifier is reported only once
mod_auth_dbm.c:110: error: for each function it appears in.)
mod_auth_dbm.c:110: error: ‘f’ undeclared (first use in this function)
mod_auth_dbm.c:111: error: ‘datum’ undeclared (first use in this function)
mod_auth_dbm.c:111: error: syntax error before ‘d’
mod_auth_dbm.c:114: error: ‘q’ undeclared (first use in this function)
mod_auth_dbm.c:128: error: ‘d’ undeclared (first use in this function)
make[4]: *** [mod_auth_dbm.so] Error 1
make[3]: *** [all] Error 1
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/tmp/apache_1.3.37/src'
make[1]: *** [build-std] Error 2
make[1]: Leaving directory `/tmp/apache_1.3.37'
make: *** [build] Error 2
elow@ubuntu:/tmp/apache_1.3.37$

---

### Post by WW on 2007-03-31
The first error says that you are missing the header file "ndbm.h".  Try installing the package **libgdbm3-dev**.

By the way, there is no need to use **sudo** when you run **make** with no other target. You will only need sudo when you run **sudo make install**.

---

