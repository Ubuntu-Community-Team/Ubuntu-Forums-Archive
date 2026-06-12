---
title: "Can someone port/compile bmpanel to work with Ubuntu?"
date: 2008-06-27
forum: The Cafe
---

### Post by PrimoTurbo on 2008-06-27
[http://nsf.110mb.com/bmpanel/](http://nsf.110mb.com/bmpanel/)

I cannot compile it.

> C: src/bmpanel.c
src/bmpanel.c:11:25: warning: sys/timerfd.h: No such file or directory
src/bmpanel.c: In function ‘init_and_start_loop’:
src/bmpanel.c:1435: warning: implicit declaration of function ‘timerfd_create’
src/bmpanel.c:1435: error: ‘CLOCK_MONOTONIC’ undeclared (first use in this function)
src/bmpanel.c:1435: error: (Each undeclared identifier is reported only once
src/bmpanel.c:1435: error: for each function it appears in.)
src/bmpanel.c:1443: error: variable ‘tspec’ has initialiser but incomplete type
src/bmpanel.c:1443: error: extra curly bracket group at end of initialiser
src/bmpanel.c:1443: error: (near initialisation for ‘tspec’)
src/bmpanel.c:1443: warning: excess elements in struct initialiser
src/bmpanel.c:1443: warning: (near initialisation for ‘tspec’)
src/bmpanel.c:1443: error: extra curly bracket group at end of initialiser
src/bmpanel.c:1443: error: (near initialisation for ‘tspec’)
src/bmpanel.c:1443: warning: excess elements in struct initialiser
src/bmpanel.c:1443: warning: (near initialisation for ‘tspec’)
src/bmpanel.c:1443: error: storage size of ‘tspec’ isn’t known
src/bmpanel.c:1444: warning: implicit declaration of function ‘timerfd_settime’
src/bmpanel.c:1443: warning: unused variable ‘tspec’
make: *** [.mk/build/src/bmpanel.o] Error 1

Thanks for any help.

---

### Post by urukrama on 2008-06-28
You can't install it on Ubuntu, because you need a more upto date version of gcc and the developer seems to think non-rolling-release distros (which have the latest gcc version installed) are not worth his attention :-)

From [this post]("http://bbs.archlinux.org/viewtopic.php?pid=385896#p385896") on the Arch forums:

> This feature called timerfd (file descriptor representing timer) appeared only 4 months ago in glibc. So your linux distribution should use glibc from CVS, because the latest official release of glibc was 2.7 and there is no such feature. I'm sorry, but I don't want to support *old* systems. Change your linux distribution to archlinux or other *good* linux distribution.

EDIT: shouldn't this be in another forum than the Café?

---

