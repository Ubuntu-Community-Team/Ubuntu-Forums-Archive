---
title: "Compiling Sun Grid Engine"
date: 2008-09-07
forum: Server Platforms
---

### Post by erik.lonroth on 2008-09-07
Hello!

I'm trying to compile the Sun Grid Engine to see if its possible to get it running on Ubuntu and possibly create some packages for it.

I've run into some basic compiling issue as shows below that I need some help resolving: 

Help greatly appreciated.

[I]Building in directory: /home/erik/sun/gridengine/source
making in LINUX86_26/ for LINUX86 at host ubuntu0
_________C_O_R_E__S_Y_S_T_E_M_____________
gcc -O3 -Wall -Werror -Wstrict-prototypes -D__GRIDENGINE_FD_SETSIZE=8192 -DLINUX -DLINUX86 -DLINUX86_26 -D_GNU_SOURCE -DGETHOSTBYNAME_R6 -DGETHOSTBYADDR_R8  -DLOAD_OPENSSL -I/usr/lib/include//usr/include -DSGE_ARCH_STRING=lx26-x86 -DTARGET_32BIT  -DSPOOLING_dynamic -DSECURE -I/off_home/gridengine/openssl-0.9.8h-origin/lx26-x86/include -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -DCOMPILE_DC -D__SGE_COMPILE_WITH_GETTEXT__  -D__SGE_NO_USERMAPPING__ -I../common -I../libs -I../libs/uti -I../libs/juti -I../libs/gdi -I../libs/japi -I../libs/sgeobj -I../libs/cull -I../libs/rmon -I../libs/comm -I../libs/comm/lists -I../libs/sched -I../libs/evc -I../libs/evm -I../libs/mir -I../libs/lck -I../daemons/common -I../daemons/qmaster -I../daemons/execd -I../daemons/schedd -I../clients/common -I. -I/usr/include -I/usr/include/linux -fPIC -c ../libs/sgeobj/config.c
In file included from /usr/include/stdio.h:75,
                 from ../libs/sgeobj/config.c:34:
/usr/include/libio.h:332: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/libio.h:364: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:373: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:493: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_IO_sgetn’
In file included from ../libs/sgeobj/config.c:34:
/usr/include/stdio.h:294: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:300: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:312: error: expected declaration specifiers or ‘...’ before ‘size_t’
[/I]

---

### Post by erik.lonroth on 2008-09-07
My setup btw:
[I]
erik@ubuntu0:~/sun/gridengine/source/libs$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[/I]

---

### Post by aherisanu on 2010-01-17
It's from JAVA_HOME=/usr it adds this: [I] -I/usr/include -I/usr/include/linux
[/I]Remove thisand it will work.

---

