---
title: "Requesting NetworkManager 0.4"
date: 2005-06-25
forum: Ubuntu Backports
---

### Post by Confuse on 2005-06-25
Is there any possibility of backporting NetworkManager 0.4? It'd be a great addition for Ubuntu wireless support.

---

### Post by Confuse on 2005-06-26
Sorry to bring back old topics, I guess this is too unstable/complicated to backport? Just currious as I didn't get any feedback at all from this request. Thanks.

Damian

---

### Post by mird on 2005-06-28
By the looks of it there are a number of dependancies issues... the Hoary hal and dbus libraries are out of date, and to upgrade them would neccessitate upgrading libc6.  Because of this it's very unlikely we'll see a backport.

Someone please correct me if I'm wrong tho :)

---

### Post by mlomker on 2005-09-08
[QUOTE=mird]By the looks of it there are a number of dependancies issues... the Hoary hal and dbus libraries are out of date, and to upgrade them would neccessitate upgrading libc6.  Because of this it's very unlikely we'll see a backport.
[/QUOTE]

I didn't seem to have a problem upgrading dbus and hal but it still fails to compile.  I does look like the error is related to glib2 and I've given up on it at this point...I don't understand enough to figure out all of the dependencies.

```
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../utils -I/usr/local/include/dbus-1.0 -I/usr/local/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDBUS_VERSION_MAJOR=0 -DDBUS_VERSION_MINOR=36 -DDBUS_VERSION_MICRO=2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDBUS_API_SUBJECT_TO_CHANGE -g -O2 -MT libnm_glib_la-libnm_glib.lo -MD -MP -MF .deps/libnm_glib_la-libnm_glib.Tpo -c libnm_glib.c  -fPIC -DPIC -o .libs/libnm_glib_la-libnm_glib.o
libnm_glib.c:231:2: #error "Unrecognized version of DBUS."
make[3]: *** [libnm_glib_la-libnm_glib.lo] Error 1
```

---

