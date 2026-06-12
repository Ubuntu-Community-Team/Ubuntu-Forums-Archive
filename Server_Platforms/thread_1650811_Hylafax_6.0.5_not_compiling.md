---
title: "Hylafax 6.0.5 not compiling"
date: 2010-12-22
forum: Server Platforms
---

### Post by map7 on 2010-12-22
I'm running ubuntu 10.10 32bit and I'm trying to compile Hylafax 6.0.5 (as 6.0.4 has a bug with faxgetty segfaulting).  I've used these commands


$ tar xvf hylafax-6.0.5.tar.gz
$ sudo aptitude install build-essential libtiff-dev
$ ./configure
$ make

Then I get this error:
```
In file included from Sys.h:34,
                 from Dispatcher.c++:27:
/usr/include/sys/stat.h:299: error: declaration of ‘int fchmod(int, __mode_t) throw ()’ throws different exceptions
../port.h:32: error: from previous declaration ‘int fchmod(int, mode_t)’
make[3]: *** [Dispatcher.o] Error 1
make[3]: Leaving directory `/home/marvin/hylafax-6.0.5/libhylafax'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/home/marvin/hylafax-6.0.5/libhylafax'
make[1]: *** [dirs] Error 2
make[1]: Leaving directory `/home/marvin/hylafax-6.0.5'
make: *** [default] Error 2
```

Am I missing another library?

---

### Post by map7 on 2010-12-28
Had to use this patch

```
diff --git a/configure b/configure
index e49c08f..c6976fd 100755
--- a/configure
+++ b/configure
@@ -2882,7 +2882,7 @@ BuildPortDotH()
echo '#define HAS_FCHMOD 1'
Note "... configure use of fchmod"
CheckFuncDecl fchmod 'extern int fchmod(int, mode_t);' \
- unistd.h libc.h $OSFCNH sys/stat.h
+ unistd.h $OSFCNH sys/stat.h libc.h
}
CheckFuncDecl mknod 'extern int mknod(const char*, mode_t, dev_t);' \
unistd.h sys/stat.h
```

Save this patch into a file called 'patch.configure' within the hylafax directory then run this command:
$ patch configure < patch.configure

---

