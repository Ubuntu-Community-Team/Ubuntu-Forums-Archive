---
title: "Building GnuPG from Source but running into permissions trouble"
date: 2015-08-17
forum: Security
---

### Post by thatsmyboy on 2015-08-17
I have tried unsuccessfully for a little while to build Gnu Privacy Guard from source. First I recognized the need for 4 dependencies :

[LIST]
[*]libassuan
[*]libgcrypt
[*]libgpg-error
[*]libksba
[/LIST]

I downloaded them but at some point (after running 'make install') I run into this : 

libtool: install: /usr/bin/install -c .libs/libassuan.so.0.5.1 /usr/local/lib/libassuan.so.0.5.1
/usr/bin/install: cannot create regular file '/usr/local/lib/libassuan.so.0.5.1': Permission denied

so I proceed with 'sudo make install'

but that creates symbolic links in the directory /usr/local/lib/ which have permissions (for example):

-rwxr-xr-x 1 root root     983 Aug 17 15:46 libassuan.la
lrwxrwxrwx 1 root root      18 Aug 17 15:46 libassuan.so -> libassuan.so.0.5.1
lrwxrwxrwx 1 root root      18 Aug 17 15:46 libassuan.so.0 -> libassuan.so.0.5.1
-rwxr-xr-x 1 root root  440366 Aug 17 15:46 libassuan.so.0.5.1

which later on are needing to be changed by gpg's  installer which no longer has permission to move/ remove files. 

I can't see how to allow this operation to proceed without getting more and more restrictive (because I keep having to use 'sudo' to force the installation)

Is this the expected procedure?

---

### Post by thatsmyboy on 2015-08-17
I also ran into this just now with libgcrypt

ecc-curves.c: In function '_gcry_ecc_fill_in_curve':
ecc-curves.c:394:12: error: 'GPG_ERR_UNKNOWN_CURVE' undeclared (first use in this function)
     return GPG_ERR_UNKNOWN_CURVE;
            ^
ecc-curves.c:394:12: note: each undeclared identifier is reported only once for each function it appears in
ecc-curves.c: In function '_gcry_ecc_update_curve_param':
ecc-curves.c:460:12: error: 'GPG_ERR_UNKNOWN_CURVE' undeclared (first use in this function)
     return GPG_ERR_UNKNOWN_CURVE;
            ^
make[2]: *** [ecc-curves.lo] Error 1
make[2]: Leaving directory `/home/stephen/computers/libgcrypt-1.6.3/cipher'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stephen/computers/libgcrypt-1.6.3'
make: *** [all] Error 2

---

### Post by thatsmyboy on 2015-08-17
I also ran into this just now with libgcrypt

ecc-curves.c: In function '_gcry_ecc_fill_in_curve':
ecc-curves.c:394:12: error: 'GPG_ERR_UNKNOWN_CURVE' undeclared (first use in this function)
     return GPG_ERR_UNKNOWN_CURVE;
            ^
ecc-curves.c:394:12: note: each undeclared identifier is reported only once for each function it appears in
ecc-curves.c: In function '_gcry_ecc_update_curve_param':
ecc-curves.c:460:12: error: 'GPG_ERR_UNKNOWN_CURVE' undeclared (first use in this function)
     return GPG_ERR_UNKNOWN_CURVE;
            ^
make[2]: *** [ecc-curves.lo] Error 1
make[2]: Leaving directory `/home/stephen/computers/libgcrypt-1.6.3/cipher'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stephen/computers/libgcrypt-1.6.3'
make: *** [all] Error 2

---

### Post by tgalati4 on 2015-08-18
The general procedure is:

```
./configure
make
sudo make install
```

Because you are having problems:

```
make clean
make all
```

The symbolic links in /usr/local/lib are created to fix problems when going from Debian to Ubuntu, in other words, a packaging/distro fix that is performed by a post-installation script during a *dpkg* or *apt-get *install.

Why are you trying to build GPG from source?

---

### Post by thatsmyboy on 2015-09-11
I was trying to get around the error from Enigmail / GPG version error. the version packaged by Ubuntu (1.4.16) is no longer supported by Enigmail (2.x+)

> We recommend GnuPG version 2.x; GnuPG 1.4.x is considered legacy and support for it will be dropped soon. Minimum versions required are 1.4.9 or 2.0.9, but we recommend the latest versions of GnuPG as they contain security fixes. 

---

