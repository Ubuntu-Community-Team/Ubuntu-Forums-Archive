---
title: "quagga manual installation"
date: 2015-07-26
forum: Ubuntu Application Development
---

### Post by mikael-sondi on 2015-07-26
Hello room,
I am currently trying to install quagga from source. Configure command works well , but make and make install fail with the following errors:
../lib/.libs/libzebra.so: undefined reference to `cap_get_flag'
../lib/.libs/libzebra.so: undefined reference to `cap_set_proc'
../lib/.libs/libzebra.so: undefined reference to `cap_init'
../lib/.libs/libzebra.so: undefined reference to `cap_clear'
../lib/.libs/libzebra.so: undefined reference to `cap_free'
../lib/.libs/libzebra.so: undefined reference to `cap_set_flag'
I have just decided to compile the source file into a ubuntu .deb file so as to ease the process. There too, another problem arises. does anyone know how it was done here? [http://packages.ubuntu.com/precise/quagga](http://packages.ubuntu.com/precise/quagga).
I would like to have a step by step answer to how it was done by ubuntu developers
Thanks

---

