---
title: "proftpd proftpd-1.3.2rc1 make problem"
date: 2008-08-25
forum: Server Platforms
---

### Post by [pl]ice on 2008-08-25
hi,
tried to compile proftpd, need ssl like:
 ./configure --with-modules=mod_auth_pam::mod_lang:mod_quotatab:mod_quotatab_file:mod_quotatab_sql:mod_site_misc:mod_sql:mod_tls:mod_wrap:mod_wrap2:mod_wrap2_file:mod_wrap2_sql


configure says ok,
make shows:

mod_dso.c:33:18: error: ltdl.h: No such file or directory
mod_dso.c: In function 'dso_load_file':
mod_dso.c:61: warning: implicit declaration of function 'lt_dlopenext'
mod_dso.c:61: warning: comparison between pointer and integer
mod_dso.c:63: warning: implicit declaration of function 'lt_dlerror'
mod_dso.c:63: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
mod_dso.c: In function 'dso_load_module':
mod_dso.c:74: error: 'lt_ptr' undeclared (first use in this function)
mod_dso.c:74: error: (Each undeclared identifier is reported only once
mod_dso.c:74: error: for each function it appears in.)
mod_dso.c:74: error: expected ';' before 'mh'
mod_dso.c:102: error: 'mh' undeclared (first use in this function)
mod_dso.c:107: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
mod_dso.c:111: warning: implicit declaration of function 'lt_dlopen'
mod_dso.c:114: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
mod_dso.c:128: warning: implicit declaration of function 'lt_dlsym'
mod_dso.c:137: warning: implicit declaration of function 'lt_dlclose'
mod_dso.c: In function 'dso_unload_module':
mod_dso.c:204: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
mod_dso.c: In function 'set_modulepath':
mod_dso.c:535: warning: implicit declaration of function 'lt_dlsetsearchpath'
mod_dso.c: In function 'dso_init':
mod_dso.c:609: warning: implicit declaration of function 'LTDL_SET_PRELOADED_SYMBOLS'
mod_dso.c:612: warning: implicit declaration of function 'lt_dlinit'
mod_dso.c:614: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
mod_dso.c:621: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
At top level:
cc1: error: unrecognized command line option "-Wno-long-double"
make[1]: *** [mod_dso.o] Error 1
make[1]: Leaving directory `/etc/compiled/proftpd-1.3.2rc1/modules'
make: *** [modules] Error 2

i'm not sure which module makes that error ...

ideas?
thanks

---

### Post by getixmice on 2008-10-07
bump

---

### Post by alastair on 2008-10-07
Well, you are missing at least one header e.g.

ltdl.h: No such file or directory

Do you know what "ltdl.h" is? I did not, but a quick google jumped me to this forum (one result) :

[http://ubuntuforums.org/showthread.php?t=135024](http://ubuntuforums.org/showthread.php?t=135024)

Maybe some help.

Alastair

---

### Post by [pl]ice on 2008-10-07
thanks :)

yeh, I have managed to compile it correctly. Works ok!

---

