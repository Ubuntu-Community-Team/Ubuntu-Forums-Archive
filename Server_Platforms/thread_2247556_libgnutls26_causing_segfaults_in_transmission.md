---
title: "libgnutls26 causing segfaults in transmission"
date: 2014-10-08
forum: Server Platforms
---

### Post by jpaytoncfd on 2014-10-08
I cant get transmission to run for more then 5 minuets. It dies with a segfault relating to libgnutls26. 

[100988.858923] transmission-da[28274]: segfault at 0 ip 00007f32b7026b59 sp 00007f32b1df8930 error 4 in libgnutls.so.26.22.6[7f32b6fb2000+b6000]

I have tried everything I can think of with transmission. Purged, removed config files, started it with upstart and command line. I have seen several bugs relating to the libgnutls26 causing segfaults. The general solution is to change versions but none are available besides the current. This lists several used applications as needing this package so I guess I cant get rid of it. Any other options?

---

### Post by jpaytoncfd on 2014-10-09
I found one previous version but it wants to uninstall ubuntu-minimal among other things.

---

### Post by jpaytoncfd on 2014-10-09
I got a different version. I tried older and newer. no change. I am out of ideas...

---

