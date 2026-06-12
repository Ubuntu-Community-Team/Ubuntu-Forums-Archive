---
title: "where is imlib2?"
date: 2004-12-18
forum: Repositories &amp; Backports
---

### Post by GNUmonkey on 2004-12-18
Now, i'm gonna try not to sound like an eejit while asking this question, but.... where can i find an ubuntu specific package of imlib2? Tried to apt-get it, but was told its not available. Am i gonna have to go to the enlightenment website and get a package from there?

Thanks for any help you can give

Chris

---

### Post by WW on 2004-12-18
The **Search** option in Synaptic is very useful. :)

Using it to search for imlib2 turned up **libimlib2**, among other packages.

---

### Post by GNUmonkey on 2004-12-18
Yeah, i tried installing that and libimlib2-dev before i posted here, but the software i'm trying to install (PyPanel, if that makes any difference) still tells me i'm missing imlib2, which is frustrating. Thanks anyway.

---

### Post by GNUmonkey on 2004-12-18
ok, looks i've found the problem. pypanel requires imlib2 v 1.1.1, and the version in apt is 1.1.0-12. guess i'll just have to grab the sources from enlightenment.org.

Cheers

---

### Post by orengolan on 2008-05-25
I have xubuntu hardy and I can't install imlib2.
I tried imlib2-1.0.6, imlib2-1.2.0 and imlib2-1.2.2
the install has no errors (as far as I can tell) but I can't find it in dpkg -l '*imlib*' so I assume it's not installed.

for example, here is the output from sudo make install of imlib2-1.2.2 :(instructions are here - [http://www.linuxfromscratch.org/blfs/view/6.2.0/general/imlib2.html](http://www.linuxfromscratch.org/blfs/view/6.2.0/general/imlib2.html))

make install &&
install -v -m755 -d /usr/share/doc/imlib2-1.2.2 &&
install -v -m644 doc/{*.gif,index.html} \
    /usr/share/doc/imlib2-1.2.2

```

Making install in src
make[1]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src'
Making install in lib
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/lib'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/lib'
/bin/bash ../../mkinstalldirs /usr/lib
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  libImlib2.la /usr/lib/libImlib2.la
/usr/bin/install -c .libs/libImlib2.so.1.2.1 /usr/lib/libImlib2.so.1.2.1
(cd /usr/lib && { ln -s -f libImlib2.so.1.2.1 libImlib2.so.1 || { rm -f libImlib2.so.1 && ln -s libImlib2.so.1.2.1 libImlib2.so.1; }; })
(cd /usr/lib && { ln -s -f libImlib2.so.1.2.1 libImlib2.so || { rm -f libImlib2.so && ln -s libImlib2.so.1.2.1 libImlib2.so; }; })
/usr/bin/install -c .libs/libImlib2.lai /usr/lib/libImlib2.la
/usr/bin/install -c .libs/libImlib2.a /usr/lib/libImlib2.a
chmod 644 /usr/lib/libImlib2.a
ranlib /usr/lib/libImlib2.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag


   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/bin/bash ../../mkinstalldirs /usr/include
 /usr/bin/install -c -m 644 Imlib2.h /usr/include/Imlib2.h
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/lib'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/lib'
Making install in bin
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/bin'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/bin'
/bin/bash ../../mkinstalldirs /usr/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_conv /usr/bin/imlib2_conv
/usr/bin/install -c .libs/imlib2_conv /usr/bin/imlib2_conv
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_show /usr/bin/imlib2_show
/usr/bin/install -c .libs/imlib2_show /usr/bin/imlib2_show
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_test /usr/bin/imlib2_test
/usr/bin/install -c .libs/imlib2_test /usr/bin/imlib2_test
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_bumpmap /usr/bin/imlib2_bumpmap
/usr/bin/install -c .libs/imlib2_bumpmap /usr/bin/imlib2_bumpmap
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_poly /usr/bin/imlib2_poly
/usr/bin/install -c .libs/imlib2_poly /usr/bin/imlib2_poly
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_colorspace /usr/bin/imlib2_colorspace
/usr/bin/install -c .libs/imlib2_colorspace /usr/bin/imlib2_colorspace
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_view /usr/bin/imlib2_view
/usr/bin/install -c .libs/imlib2_view /usr/bin/imlib2_view
  /bin/bash ../../libtool --mode=install /usr/bin/install -c imlib2_grab /usr/bin/imlib2_grab

/usr/bin/install -c .libs/imlib2_grab /usr/bin/imlib2_grab
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/bin'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/bin'
Making install in modules
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules'
Making install in loaders
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/loaders'
make[4]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/loaders'
make[4]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../mkinstalldirs /usr/lib/imlib2/loaders
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  png.la /usr/lib/imlib2/loaders/png.la
libtool: install: warning: relinking `png.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o png.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_png.lo -lpng -lz -lm ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_png.o  -lpng -lz -lm -L/usr/lib -lImlib2  -Wl,-soname -Wl,png.so -o .libs/png.so
/usr/bin/install -c .libs/png.soT /usr/lib/imlib2/loaders/png.so
/usr/bin/install -c .libs/png.lai /usr/lib/imlib2/loaders/png.la
/usr/bin/install -c .libs/png.a /usr/lib/imlib2/loaders/png.a
chmod 644 /usr/lib/imlib2/loaders/png.a
ranlib /usr/lib/imlib2/loaders/png.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and

specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  zlib.la /usr/lib/imlib2/loaders/zlib.la
libtool: install: warning: relinking `zlib.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o zlib.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_zlib.lo -lz ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_zlib.o  -lz -L/usr/lib -lImlib2  -Wl,-soname -Wl,zlib.so -o .libs/zlib.so
/usr/bin/install -c .libs/zlib.soT /usr/lib/imlib2/loaders/zlib.so
/usr/bin/install -c .libs/zlib.lai /usr/lib/imlib2/loaders/zlib.la
/usr/bin/install -c .libs/zlib.a /usr/lib/imlib2/loaders/zlib.a
chmod 644 /usr/lib/imlib2/loaders/zlib.a
ranlib /usr/lib/imlib2/loaders/zlib.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries

in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  pnm.la /usr/lib/imlib2/loaders/pnm.la
libtool: install: warning: relinking `pnm.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o pnm.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_pnm.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_pnm.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,pnm.so -o .libs/pnm.so
/usr/bin/install -c .libs/pnm.soT /usr/lib/imlib2/loaders/pnm.so
/usr/bin/install -c .libs/pnm.lai /usr/lib/imlib2/loaders/pnm.la
/usr/bin/install -c .libs/pnm.a /usr/lib/imlib2/loaders/pnm.a
chmod 644 /usr/lib/imlib2/loaders/pnm.a
ranlib /usr/lib/imlib2/loaders/pnm.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders


If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  argb.la /usr/lib/imlib2/loaders/argb.la
libtool: install: warning: relinking `argb.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o argb.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_argb.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_argb.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,argb.so -o .libs/argb.so
/usr/bin/install -c .libs/argb.soT /usr/lib/imlib2/loaders/argb.so
/usr/bin/install -c .libs/argb.lai /usr/lib/imlib2/loaders/argb.la
/usr/bin/install -c .libs/argb.a /usr/lib/imlib2/loaders/argb.a
chmod 644 /usr/lib/imlib2/loaders/argb.a
ranlib /usr/lib/imlib2/loaders/argb.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  bmp.la /usr/lib/imlib2/loaders/bmp.la
libtool: install: warning: relinking `bmp.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o bmp.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_bmp.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_bmp.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,bmp.so -o .libs/bmp.so
/usr/bin/install -c .libs/bmp.soT /usr/lib/imlib2/loaders/bmp.so
/usr/bin/install -c .libs/bmp.lai /usr/lib/imlib2/loaders/bmp.la
/usr/bin/install -c .libs/bmp.a /usr/lib/imlib2/loaders/bmp.a
chmod 644 /usr/lib/imlib2/loaders/bmp.a
ranlib /usr/lib/imlib2/loaders/bmp.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:

   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  xpm.la /usr/lib/imlib2/loaders/xpm.la
libtool: install: warning: relinking `xpm.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o xpm.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_xpm.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_xpm.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,xpm.so -o .libs/xpm.so
/usr/bin/install -c .libs/xpm.soT /usr/lib/imlib2/loaders/xpm.so
/usr/bin/install -c .libs/xpm.lai /usr/lib/imlib2/loaders/xpm.la
/usr/bin/install -c .libs/xpm.a /usr/lib/imlib2/loaders/xpm.a
chmod 644 /usr/lib/imlib2/loaders/xpm.a
ranlib /usr/lib/imlib2/loaders/xpm.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  tga.la /usr/lib/imlib2/loaders/tga.la
libtool: install: warning: relinking `tga.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o tga.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_tga.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_tga.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,tga.so -o .libs/tga.so
/usr/bin/install -c .libs/tga.soT /usr/lib/imlib2/loaders/tga.so
/usr/bin/install -c .libs/tga.lai /usr/lib/imlib2/loaders/tga.la
/usr/bin/install -c .libs/tga.a /usr/lib/imlib2/loaders/tga.a
chmod 644 /usr/lib/imlib2/loaders/tga.a
ranlib /usr/lib/imlib2/loaders/tga.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  lbm.la /usr/lib/imlib2/loaders/lbm.la
libtool: install: warning: relinking `lbm.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/loaders; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o lbm.la -rpath /usr/lib/imlib2/loaders -module -avoid-version loader_lbm.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/loader_lbm.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,lbm.so -o .libs/lbm.so
/usr/bin/install -c .libs/lbm.soT /usr/lib/imlib2/loaders/lbm.so
/usr/bin/install -c .libs/lbm.lai /usr/lib/imlib2/loaders/lbm.la
/usr/bin/install -c .libs/lbm.a /usr/lib/imlib2/loaders/lbm.a
chmod 644 /usr/lib/imlib2/loaders/lbm.a
ranlib /usr/lib/imlib2/loaders/lbm.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/loaders
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/loaders

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/loaders'
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/loaders'
Making install in filters
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/filters'
make[4]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/filters'
make[4]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../mkinstalldirs /usr/lib/imlib2/filters
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  testfilter.la /usr/lib/imlib2/filters/testfilter.la
libtool: install: warning: relinking `testfilter.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/filters; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o testfilter.la -rpath /usr/lib/imlib2/filters -module -avoid-version filter_test.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/filter_test.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,testfilter.so -o .libs/testfilter.so
/usr/bin/install -c .libs/testfilter.soT /usr/lib/imlib2/filters/testfilter.so
/usr/bin/install -c .libs/testfilter.lai /usr/lib/imlib2/filters/testfilter.la
/usr/bin/install -c .libs/testfilter.a /usr/lib/imlib2/filters/testfilter.a
chmod 644 /usr/lib/imlib2/filters/testfilter.a
ranlib /usr/lib/imlib2/filters/testfilter.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/filters
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/filters

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  bumpmap.la /usr/lib/imlib2/filters/bumpmap.la
libtool: install: warning: relinking `bumpmap.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/filters; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o bumpmap.la -rpath /usr/lib/imlib2/filters -module -avoid-version filter_bumpmap.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/filter_bumpmap.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,bumpmap.so -o .libs/bumpmap.so
/usr/bin/install -c .libs/bumpmap.soT /usr/lib/imlib2/filters/bumpmap.so
/usr/bin/install -c .libs/bumpmap.lai /usr/lib/imlib2/filters/bumpmap.la
/usr/bin/install -c .libs/bumpmap.a /usr/lib/imlib2/filters/bumpmap.a
chmod 644 /usr/lib/imlib2/filters/bumpmap.a
ranlib /usr/lib/imlib2/filters/bumpmap.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/filters
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/filters

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  colormod.la /usr/lib/imlib2/filters/colormod.la
libtool: install: warning: relinking `colormod.la'
(cd /home/oren/Desktop/imlib2-1.2.2/src/modules/filters; /bin/bash ../../../libtool  --mode=relink gcc -g -O2 -o colormod.la -rpath /usr/lib/imlib2/filters -module -avoid-version filter_colormod.lo ../../../src/lib/libImlib2.la )
gcc -shared  .libs/filter_colormod.o  -L/usr/lib -lImlib2  -Wl,-soname -Wl,colormod.so -o .libs/colormod.so
/usr/bin/install -c .libs/colormod.soT /usr/lib/imlib2/filters/colormod.so
/usr/bin/install -c .libs/colormod.lai /usr/lib/imlib2/filters/colormod.la
/usr/bin/install -c .libs/colormod.a /usr/lib/imlib2/filters/colormod.a
chmod 644 /usr/lib/imlib2/filters/colormod.a
ranlib /usr/lib/imlib2/filters/colormod.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/imlib2/filters
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/imlib2/filters

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/filters'
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules/filters'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules'
make[4]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src/modules'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules'
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src/modules'
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/src'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src'
make[1]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/src'
Making install in data
make[1]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data'
Making install in fonts
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data/fonts'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data/fonts'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/share/imlib2/data/fonts
 /usr/bin/install -c -m 644 cinema.ttf /usr/share/imlib2/data/fonts/cinema.ttf
 /usr/bin/install -c -m 644 grunge.ttf /usr/share/imlib2/data/fonts/grunge.ttf
 /usr/bin/install -c -m 644 morpheus.ttf /usr/share/imlib2/data/fonts/morpheus.ttf
 /usr/bin/install -c -m 644 notepad.ttf /usr/share/imlib2/data/fonts/notepad.ttf
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data/fonts'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data/fonts'
Making install in images
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data/images'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data/images'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/share/imlib2/data/images
 /usr/bin/install -c -m 644 audio.png /usr/share/imlib2/data/images/audio.png
 /usr/bin/install -c -m 644 bg.png /usr/share/imlib2/data/images/bg.png
 /usr/bin/install -c -m 644 bulb.png /usr/share/imlib2/data/images/bulb.png
 /usr/bin/install -c -m 644 cal.png /usr/share/imlib2/data/images/cal.png
 /usr/bin/install -c -m 644 calc.png /usr/share/imlib2/data/images/calc.png
 /usr/bin/install -c -m 644 folder.png /usr/share/imlib2/data/images/folder.png
 /usr/bin/install -c -m 644 globe.png /usr/share/imlib2/data/images/globe.png
 /usr/bin/install -c -m 644 imlib2.png /usr/share/imlib2/data/images/imlib2.png
 /usr/bin/install -c -m 644 lock.png /usr/share/imlib2/data/images/lock.png
 /usr/bin/install -c -m 644 mail.png /usr/share/imlib2/data/images/mail.png
 /usr/bin/install -c -m 644 menu.png /usr/share/imlib2/data/images/menu.png
 /usr/bin/install -c -m 644 mush.png /usr/share/imlib2/data/images/mush.png
 /usr/bin/install -c -m 644 paper.png /usr/share/imlib2/data/images/paper.png
 /usr/bin/install -c -m 644 sh1.png /usr/share/imlib2/data/images/sh1.png
 /usr/bin/install -c -m 644 sh2.png /usr/share/imlib2/data/images/sh2.png
 /usr/bin/install -c -m 644 sh3.png /usr/share/imlib2/data/images/sh3.png
 /usr/bin/install -c -m 644 stop.png /usr/share/imlib2/data/images/stop.png
 /usr/bin/install -c -m 644 tnt.png /usr/share/imlib2/data/images/tnt.png
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data/images'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data/images'
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data'
make[3]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/data'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data'
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data'
make[1]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/data'
Making install in doc
make[1]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/doc'
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/doc'
make[1]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2/doc'
make[1]: Entering directory `/home/oren/Desktop/imlib2-1.2.2'
make[2]: Entering directory `/home/oren/Desktop/imlib2-1.2.2'
/bin/bash ./mkinstalldirs /usr/bin
 /usr/bin/install -c imlib2-config /usr/bin/imlib2-config
/bin/bash ./mkinstalldirs /usr/lib/pkgconfig
 /usr/bin/install -c -m 644 imlib2.pc /usr/lib/pkgconfig/imlib2.pc
make[2]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2'
make[1]: Leaving directory `/home/oren/Desktop/imlib2-1.2.2'
removed `/usr/share/doc/imlib2-1.2.2/blank.gif'
`doc/blank.gif' -> `/usr/share/doc/imlib2-1.2.2/blank.gif'
removed `/usr/share/doc/imlib2-1.2.2/imlib2.gif'
`doc/imlib2.gif' -> `/usr/share/doc/imlib2-1.2.2/imlib2.gif'
removed `/usr/share/doc/imlib2-1.2.2/index.html'
`doc/index.html' -> `/usr/share/doc/imlib2-1.2.2/index.html'


```

---

### Post by WW on 2008-05-25
The packages in hardy are [libimlib2](http://packages.ubuntu.com/hardy/libimlib2) and, if you are compiling something that needs imlib2, [libimlib2-dev](http://packages.ubuntu.com/hardy/libimlib2-dev).  Are you saying you couldn't install these packages?

---

### Post by orengolan on 2008-05-26
I installed successfully libimlib2 and libimlib2-dev but 
when I try to install awesome window manager 2.3 I get this:
```
configure: error: awesome requires Imlib2.
```

any idea?

---

### Post by orengolan on 2008-05-26
i solved my issue - i configured the app with gtk instead of Imlib2:
/configure --with-gtk 

btw, I installed awesome window manager, it's a lightweight manager that looks very interesting.
[http://awesome.naquadah.org/](http://awesome.naquadah.org/)

---

### Post by darius007 on 2011-07-21
I installed libImlib2, but I am still getting an error:

error while loading shared libraries: libImlib2.so.1: wrong ELF class: ELFCLASS64

I think this probably has to do with ubuntu x64 ELF class, though I appreciate if someone please let me know how I can get the right library installed.

---

