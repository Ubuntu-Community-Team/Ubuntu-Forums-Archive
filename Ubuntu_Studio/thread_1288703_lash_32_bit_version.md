---
title: "lash 32 bit version"
date: 2009-10-11
forum: Ubuntu Studio
---

### Post by c00kie55 on 2009-10-11
hi cut someone tell me howto ? build lash 32 bit on karmic desktop 64 bit

i tryed this command
 CC="gcc-4.4 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v

and it configures ok but when i run make this comes up

 make
make  all-recursive
make[1]: Entering directory `/home/gorm/lash5'
Making all in m4
make[2]: Entering directory `/home/gorm/lash5/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gorm/lash5/m4'
Making all in docs
make[2]: Entering directory `/home/gorm/lash5/docs'
Making all in lash-manual-html-one-page
make[3]: Entering directory `/home/gorm/lash5/docs/lash-manual-html-one-page'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/gorm/lash5/docs/lash-manual-html-one-page'
Making all in lash-manual-html-split
make[3]: Entering directory `/home/gorm/lash5/docs/lash-manual-html-split'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/gorm/lash5/docs/lash-manual-html-split'
make[3]: Entering directory `/home/gorm/lash5/docs'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/gorm/lash5/docs'
make[2]: Leaving directory `/home/gorm/lash5/docs'
Making all in lash
make[2]: Entering directory `/home/gorm/lash5/lash'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gorm/lash5/lash'
Making all in liblash
make[2]: Entering directory `/home/gorm/lash5/liblash'
if /bin/bash ../libtool --tag=CC --mode=compile gcc-4.4 -m32 -DHAVE_CONFIG_H -I. -I. -I..  -I..  -DLASH_BUILD -DHAVE_LASH -g -O2 -MT liblash_la-socket.lo -MD -MP -MF ".deps/liblash_la-socket.Tpo" -c -o liblash_la-socket.lo `test -f 'socket.c' || echo './'`socket.c; \
    then mv -f ".deps/liblash_la-socket.Tpo" ".deps/liblash_la-socket.Plo"; else rm -f ".deps/liblash_la-socket.Tpo"; exit 1; fi
 gcc-4.4 -m32 -DHAVE_CONFIG_H -I. -I. -I.. -I.. -DLASH_BUILD -DHAVE_LASH -g -O2 -MT liblash_la-socket.lo -MD -MP -MF .deps/liblash_la-socket.Tpo -c socket.c  -fPIC -DPIC -o .libs/liblash_la-socket.o
In file included from ../lash/list.h:37,
                 from socket.c:36:
../lash/xmalloc.h: In function 'lash_strdup':
../lash/xmalloc.h:51: warning: incompatible implicit declaration of built-in function 'strdup'
socket.c: In function 'lash_lookup_peer_name':
socket.c:266: error: 'NI_MAXHOST' undeclared (first use in this function)
socket.c:266: error: (Each undeclared identifier is reported only once
socket.c:266: error: for each function it appears in.)
socket.c: In function 'lash_lookup_peer_port':
socket.c:279: error: 'NI_MAXSERV' undeclared (first use in this function)
make[2]: *** [liblash_la-socket.lo] Error 1
make[2]: Leaving directory `/home/gorm/lash5/liblash'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gorm/lash5'
make: *** [all] Error 2

thanx in advance for any help

---

### Post by c00kie55 on 2009-10-11
by the way above post is lash 0.5.4

lash-0.6.0.594 cant configure return missing python 2.3

/lash6$ CC="gcc-4.4 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc-4.4 -m32
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc-4.4 -m32 accepts -g... yes
checking for gcc-4.4 -m32 option to accept ISO C89... none needed
checking dependency style of gcc-4.4 -m32... gcc3
checking whether gcc-4.4 -m32 and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc-4.4 -m32... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc-4.4 -m32 -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc-4.4 -m32 object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc-4.4 -m32 supports -fno-rtti -fno-exceptions... no
checking for gcc-4.4 -m32 option to produce PIC... -fPIC
checking if gcc-4.4 -m32 PIC flag -fPIC works... yes
checking if gcc-4.4 -m32 static flag -static works... yes
checking if gcc-4.4 -m32 supports -c -o file.o... yes
checking whether the gcc-4.4 -m32 linker (/usr/bin/ld -m elf_i386) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_i386
checking if the linker (/usr/bin/ld -m elf_i386) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_i386) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... no
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_i386) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether to enable debugging output... no
checking whether to enable the old API... yes
checking whether to use D-Bus for JACK communication... yes
checking whether to build with ALSA MIDI support... auto
checking whether to build clients which require GTK+ 2... auto
checking whether to build Python bindings... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... yes
checking for DBUS... yes
checking for UUID... yes
checking for XML2... yes
checking for ALSA... yes
checking for snd_seq_open... yes
checking for GTK2... yes
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for headers required to compile python extensions... not found

  The following optionally selected dependencies are missing from your system:

    Python >= 2.3

  Please refer to these websites for further information:

    Python:   [http://www.python.org/](http://www.python.org/)

configure: error: Missing packages

i cant find no python2.3-dev in repos

---

