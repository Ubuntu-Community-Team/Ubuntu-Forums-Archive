---
title: "mod_ctrls_admin proFTPD problem"
date: 2008-08-29
forum: Server Platforms
---

### Post by [pl]ice on 2008-08-29
hi guys
i'm trying to ./configure --enable-ctrls --with-modules=mod_clamav:mod_ban:mod_msg:mod_tls

mod_ban needs --enable-ctrls but i get error messages like:


make[1]: Entering directory `/etc/compiled/proftpd-1.3.2rc1/lib'
make[1]: Nothing to be done for `lib'.
make[1]: Leaving directory `/etc/compiled/proftpd-1.3.2rc1/lib'
cd src/ && make src
make[1]: Entering directory `/etc/compiled/proftpd-1.3.2rc1/src'
make[1]: Nothing to be done for `src'.
make[1]: Leaving directory `/etc/compiled/proftpd-1.3.2rc1/src'
cd modules/ && make static
make[1]: Entering directory `/etc/compiled/proftpd-1.3.2rc1/modules'
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c mod_ban.c
mod_ban.c: In function 'ban_startup_ev':
mod_ban.c:1922: error: too few arguments to function 'pr_timer_add'
At top level:
cc1: error: unrecognize  command line option "-Wno-long-double"
make[1]: *** [mod_ban.o] Error 1
make[1]: Leaving directory `/etc/compiled/proftpd-1.3.2rc1/modules'
make: *** [modules] Error 2



ie i think i don't have that ctrls ... whats the deal with that? i got latest .gz package of proftpd.
anybody?
thank you

---

