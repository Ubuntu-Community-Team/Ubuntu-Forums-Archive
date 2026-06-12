---
title: "idevicerestore installation error"
date: 2015-11-15
forum: Ubuntu Phone and Tablet
---

### Post by vento2 on 2015-11-15
Hi, have experienced trouble with idevicerestore installation. I'm struggling for half day, and still got no solution :(:(:(:(:(
./configure command goes fine, but when I run make.....

restore.c:874:18: error: too few arguments to function &#8216;restored_start_restore&#8217;
  restore_error = restored_start_restore(restore);
                  ^
In file included from restore.c:25:0:
/usr/include/libimobiledevice/restore.h:64:18: note: declared here
 restored_error_t restored_start_restore(restored_client_t client, plist_t optio
                  ^
Makefile:583: istruction set for object "idevicerestore-restore.o" failed
make[2]: *** [idevicerestore-restore.o] Errore 1
make[2]: uscita dalla directory "/home/vento/Scrivania/idevicerestore/idevicerestore/src"
Makefile:411: istruction set for object "all-recursive" failed
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory "/home/vento/Scrivania/idevicerestore/idevicerestore"
Makefile:343: istruction set for object "all" failed
make: *** [all] Errore 2
 
Please help me, I have iPhone 5c offline, and I'm trying to restore with idevicerestore since iTunes gives me all kind of errors and doesn't let me update or restore my device.

Thank you

---

### Post by Vladlenin5000 on 2015-11-15
Please check the updated instructions in the first comment [here]("https://www.icj.me/tutorials/compile-idevicerestore-on-linux").

---

### Post by vento2 on 2015-11-15
I even followed updated procedure, but still got the same error... what should I do?

---

