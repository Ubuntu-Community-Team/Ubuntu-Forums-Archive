---
title: "Issue installing mod_perl"
date: 2011-04-12
forum: Server Platforms
---

### Post by RagnarIV on 2011-04-12
Hey guys,

I'm installing mod_perl and when running the make test I got the following errors:


	-o mod_perl.so
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[1]: *** [mod_perl.so] Error 1
make[1]: Leaving directory `/home/alan/mod_perl-2.0.5/src/modules/perl'
make: *** [modperl_lib] Error 2

So as this is the first time I have tried developing with mod_perl I tried googling the error and -lperl and I can't seem to find anything any ideas?

---

### Post by RagnarIV on 2011-04-12
I've done some digging and it looks like I am missing a symbolic link somewhere. I'll update later once I fix it.

---

### Post by RagnarIV on 2011-06-05
I managed to work around this by installing mod_perl from the synaptic package manager. Went by w/o any issues after I did that.

---

