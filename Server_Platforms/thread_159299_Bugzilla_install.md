---
title: "Bugzilla install"
date: 2006-04-12
forum: Server Platforms
---

### Post by thedima on 2006-04-12
I am trying to install bugzilla on a dev server and am running into a problem with the needed perl modules. Ive installed all the required ones besides Template. When I try to install Template (automatically and manually) I get the following error:


make[1]: Entering directory `/root/.cpan/build/Template-Toolkit-2.14/xs'
/usr/bin/perl /usr/share/perl/5.8.7/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap  Stash.xs > Stash.xsc && mv Stash.xsc Stash.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"2.14\" -DXS_VERSION=\"2.14\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Stash.c
/bin/sh: cc: command not found
make[1]: *** [Stash.o] Error 127
make[1]: Leaving directory `/root/.cpan/build/Template-Toolkit-2.14/xs'
make: *** [subdirs] Error 2
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


Does anyone know whats going wrong?

---

