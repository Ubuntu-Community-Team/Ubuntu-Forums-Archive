---
title: "php segfault"
date: 2008-12-27
forum: Server Platforms
---

### Post by superheavy on 2008-12-27
I am running 8.10 server edition.  I need to use php but it always crashes with a segfault, even with```
 php - v
```. I would post the stack trace but it is HUGE.  Here is the last bit when it crashed from the command "php -v".

```

Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies
) = 183
open("/dev/urandom", O_RDONLY)          = 3
read(3, "\201\255\177\363", 4)          = 4
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "\321\272 \323", 4)             = 4
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "\301\253\177\f", 4)            = 4
close(3)                                = 0
setitimer(ITIMER_PROF, {it_interval={0, 0}, it_value={0, 0}}, NULL) = 0
futex(0xb751cbac, FUTEX_WAIT, 2, NULL)  = 0
munmap(0xb7528000, 29352)               = 0
munmap(0xb7530000, 93148)               = 0
gettimeofday({1230366986, 878361}, NULL) = 0
munmap(0xb7547000, 105200)              = 0
munmap(0xb7747000, 47616)               = 0
munmap(0xb7561000, 1986820)             = 0
+++ killed by SIGSEGV +++
Process 22076 detached

```

Thank you for your help.

---

