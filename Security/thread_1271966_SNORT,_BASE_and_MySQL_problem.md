---
title: "SNORT, BASE and MySQL problem"
date: 2009-09-21
forum: Security
---

### Post by bprof on 2009-09-21
Hello 

I followed the steps in this thread [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472) (awesome tutorial BTW).

The problem appears when I enable the following in /etc/snort/snort.conf

[PHP]output database: log, mysql, user=snort password=snort_password dbname=snort host=localhost[/PHP]

When I run snort I get the following error:

database: ‘mysql’ support is not compiled into this build of snort
ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
‘mysql’ support.
If this build of snort was compiled by you, then re-run the
the ./configure script using the ‘—with-mysql’ switch.

I did compile snort with mysql support (--with-mysql) mysql is working. The snort database is there and everything.

Can anyone help me understand why this error is happening?

Thanks,

---

### Post by Sarmacid on 2009-09-23
Have you tried copiling snort again?

You can also try installing the package instead of compiling snort```
sudo apt-get install snort-mysql
```

---

### Post by bprof on 2009-09-23
Thanks.

I did recompile with mysql multiple times but it **failed**. The reason why I want to compile it rather than use the repos is because the version in repos is old and has some bugs that were fixed in the latest version.

So I'm not sure what to do now?

---

### Post by Sarmacid on 2009-09-23
Post the output when you try to compile snort, it's probably just some dependency issues.

---

### Post by bprof on 2009-09-23
Here is the compilation output:

```
./configure --with-mysql
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dependency style of g++... none
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ranlib... (cached) ranlib
checking whether byte ordering is bigendian... no
checking for bison... bison
checking for flex... flex
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for inttypes.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for floor in -lm... yes
checking for ceil in -lm... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking whether printf must be declared... no
checking whether fprintf must be declared... no
checking whether syslog must be declared... no
checking whether puts must be declared... no
checking whether fputs must be declared... no
checking whether fputc must be declared... no
checking whether fopen must be declared... no
checking whether fclose must be declared... no
checking whether fwrite must be declared... no
checking whether fflush must be declared... no
checking whether getopt must be declared... no
checking whether bzero must be declared... no
checking whether bcopy must be declared... no
checking whether memset must be declared... no
checking whether strtol must be declared... no
checking whether strcasecmp must be declared... no
checking whether strncasecmp must be declared... no
checking whether strerror must be declared... no
checking whether perror must be declared... no
checking whether socket must be declared... no
checking whether sendto must be declared... no
checking whether vsnprintf must be declared... no
checking whether snprintf must be declared... no
checking whether strtoul must be declared... no
checking for snprintf... yes
checking for strlcpy... no
checking for strlcat... no
checking for strerror... yes
checking for vswprintf... yes
checking for wprintf... yes
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long int... yes
checking size of long int... 4
checking for long long int... yes
checking size of long long int... 8
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long int... yes
checking size of unsigned long int... 4
checking for unsigned long long int... yes
checking size of unsigned long long int... 8
checking for u_int8_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for u_int64_t... yes
checking for uint8_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for int8_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for INADDR_NONE... yes
checking for __FUNCTION__... yes
checking for pcap_datalink in -lpcap... yes
checking for libpcap version >= 0.9... yes
checking for libpcap version 0.9.0 - 0.9.4... no
checking pcre.h usability... yes
checking pcre.h presence... yes
checking for pcre.h... yes
checking for pcre_compile in -lpcre... yes
checking for libpcre version 6.0 or greater... yes
checking for sparc... no
checking for visibility support... yes
checking for dlsym in -ldl... yes
checking for mysql... yes
checking for compress in -lz... yes
checking for mysql default client reconnect... no
checking for mysql reconnect option... yes
checking for mysql setting of reconnect option before connect bug... no
checking for linuxthreads... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating snort.pc
config.status: WARNING:  snort.pc.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/sfutil/Makefile
config.status: creating src/detection-plugins/Makefile
config.status: creating src/dynamic-plugins/Makefile
config.status: creating src/dynamic-plugins/sf_engine/Makefile
config.status: creating src/dynamic-plugins/sf_engine/examples/Makefile
config.status: creating src/dynamic-plugins/sf_preproc_example/Makefile
config.status: creating src/dynamic-preprocessors/Makefile
config.status: creating src/dynamic-preprocessors/libs/Makefile
config.status: creating src/dynamic-preprocessors/ftptelnet/Makefile
config.status: creating src/dynamic-preprocessors/smtp/Makefile
config.status: creating src/dynamic-preprocessors/ssh/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc2/Makefile
config.status: creating src/dynamic-preprocessors/dns/Makefile
config.status: creating src/dynamic-preprocessors/ssl/Makefile
config.status: creating src/output-plugins/Makefile
config.status: creating src/preprocessors/Makefile
config.status: creating src/preprocessors/HttpInspect/Makefile
config.status: creating src/preprocessors/HttpInspect/include/Makefile
config.status: creating src/preprocessors/HttpInspect/utils/Makefile
config.status: creating src/preprocessors/HttpInspect/anomaly_detection/Makefile
config.status: creating src/preprocessors/HttpInspect/client/Makefile
config.status: creating src/preprocessors/HttpInspect/event_output/Makefile
config.status: creating src/preprocessors/HttpInspect/mode_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/normalization/Makefile
config.status: creating src/preprocessors/HttpInspect/server/Makefile
config.status: creating src/preprocessors/HttpInspect/session_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/user_interface/Makefile
config.status: creating src/preprocessors/Stream5/Makefile
config.status: creating src/parser/Makefile
config.status: creating src/target-based/Makefile
config.status: creating doc/Makefile
config.status: creating contrib/Makefile
config.status: creating schemas/Makefile
config.status: creating rpm/Makefile
config.status: creating preproc_rules/Makefile
config.status: creating m4/Makefile
config.status: creating etc/Makefile
config.status: creating templates/Makefile
config.status: creating src/win32/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
```

Thanks

---

### Post by Sarmacid on 2009-09-23
Is that the whole output? I don't see the make or make install commands

You're missing a parameter from the guide```
./configure -enable-dynamicplugin --with-mysql
```

---

### Post by bprof on 2009-09-24
Sorry about that. Here is the full output:

```
./configure -enable-dynamicplugin --with-mysql && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dependency style of g++... none
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ranlib... (cached) ranlib
checking whether byte ordering is bigendian... no
checking for bison... bison
checking for flex... flex
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for inttypes.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for floor in -lm... yes
checking for ceil in -lm... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking whether printf must be declared... no
checking whether fprintf must be declared... no
checking whether syslog must be declared... no
checking whether puts must be declared... no
checking whether fputs must be declared... no
checking whether fputc must be declared... no
checking whether fopen must be declared... no
checking whether fclose must be declared... no
checking whether fwrite must be declared... no
checking whether fflush must be declared... no
checking whether getopt must be declared... no
checking whether bzero must be declared... no
checking whether bcopy must be declared... no
checking whether memset must be declared... no
checking whether strtol must be declared... no
checking whether strcasecmp must be declared... no
checking whether strncasecmp must be declared... no
checking whether strerror must be declared... no
checking whether perror must be declared... no
checking whether socket must be declared... no
checking whether sendto must be declared... no
checking whether vsnprintf must be declared... no
checking whether snprintf must be declared... no
checking whether strtoul must be declared... no
checking for snprintf... yes
checking for strlcpy... no
checking for strlcat... no
checking for strerror... yes
checking for vswprintf... yes
checking for wprintf... yes
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long int... yes
checking size of long int... 4
checking for long long int... yes
checking size of long long int... 8
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long int... yes
checking size of unsigned long int... 4
checking for unsigned long long int... yes
checking size of unsigned long long int... 8
checking for u_int8_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for u_int64_t... yes
checking for uint8_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for int8_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for INADDR_NONE... yes
checking for __FUNCTION__... yes
checking for pcap_datalink in -lpcap... yes
checking for libpcap version >= 0.9... yes
checking for libpcap version 0.9.0 - 0.9.4... no
checking pcre.h usability... yes
checking pcre.h presence... yes
checking for pcre.h... yes
checking for pcre_compile in -lpcre... yes
checking for libpcre version 6.0 or greater... yes
checking for sparc... no
checking for visibility support... yes
checking for dlsym in -ldl... yes
checking for mysql... yes
checking for compress in -lz... yes
checking for mysql default client reconnect... no
checking for mysql reconnect option... yes
checking for mysql setting of reconnect option before connect bug... no
checking for linuxthreads... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating snort.pc
config.status: WARNING:  snort.pc.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/sfutil/Makefile
config.status: creating src/detection-plugins/Makefile
config.status: creating src/dynamic-plugins/Makefile
config.status: creating src/dynamic-plugins/sf_engine/Makefile
config.status: creating src/dynamic-plugins/sf_engine/examples/Makefile
config.status: creating src/dynamic-plugins/sf_preproc_example/Makefile
config.status: creating src/dynamic-preprocessors/Makefile
config.status: creating src/dynamic-preprocessors/libs/Makefile
config.status: creating src/dynamic-preprocessors/ftptelnet/Makefile
config.status: creating src/dynamic-preprocessors/smtp/Makefile
config.status: creating src/dynamic-preprocessors/ssh/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc2/Makefile
config.status: creating src/dynamic-preprocessors/dns/Makefile
config.status: creating src/dynamic-preprocessors/ssl/Makefile
config.status: creating src/output-plugins/Makefile
config.status: creating src/preprocessors/Makefile
config.status: creating src/preprocessors/HttpInspect/Makefile
config.status: creating src/preprocessors/HttpInspect/include/Makefile
config.status: creating src/preprocessors/HttpInspect/utils/Makefile
config.status: creating src/preprocessors/HttpInspect/anomaly_detection/Makefile
config.status: creating src/preprocessors/HttpInspect/client/Makefile
config.status: creating src/preprocessors/HttpInspect/event_output/Makefile
config.status: creating src/preprocessors/HttpInspect/mode_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/normalization/Makefile
config.status: creating src/preprocessors/HttpInspect/server/Makefile
config.status: creating src/preprocessors/HttpInspect/session_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/user_interface/Makefile
config.status: creating src/preprocessors/Stream5/Makefile
config.status: creating src/parser/Makefile
config.status: creating src/target-based/Makefile
config.status: creating doc/Makefile
config.status: creating contrib/Makefile
config.status: creating schemas/Makefile
config.status: creating rpm/Makefile
config.status: creating preproc_rules/Makefile
config.status: creating m4/Makefile
config.status: creating etc/Makefile
config.status: creating templates/Makefile
config.status: creating src/win32/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/tmp/snort-2.8.5'
Making all in src
make[2]: Entering directory `/tmp/snort-2.8.5/src'
Making all in sfutil
make[3]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
Making all in win32
make[3]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/win32'
Making all in output-plugins
make[3]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
Making all in detection-plugins
make[3]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make  all-am
make[4]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
Making all in dynamic-plugins
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making all in sf_engine
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make  all-recursive
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making all in examples
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making all in sf_preproc_example
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making all in preprocessors
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
Making all in HttpInspect
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making all in include
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
Making all in utils
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
Making all in user_interface
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
Making all in session_inspection
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
Making all in mode_inspection
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
Making all in anomaly_detection
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
Making all in event_output
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
Making all in server
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
Making all in client
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
Making all in normalization
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making all in Stream5
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
Making all in parser
make[3]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/parser'
Making all in dynamic-preprocessors
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make  all-recursive
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making all in libs
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
Making all in ftptelnet
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make  all-recursive
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[8]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ftptelnet_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0 || { rm -f libsf_ftptelnet_preproc.so.0 && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so || { rm -f libsf_ftptelnet_preproc.so && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[8]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
Making all in smtp
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_smtp_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
/usr/bin/install -c .libs/libsf_smtp_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0 || { rm -f libsf_smtp_preproc.so.0 && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so || { rm -f libsf_smtp_preproc.so && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so; }; })
/usr/bin/install -c .libs/libsf_smtp_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la
/usr/bin/install -c .libs/libsf_smtp_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
Making all in ssh
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssh_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
/usr/bin/install -c .libs/libsf_ssh_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0 || { rm -f libsf_ssh_preproc.so.0 && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so || { rm -f libsf_ssh_preproc.so && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssh_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la
/usr/bin/install -c .libs/libsf_ssh_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
Making all in dcerpc
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dcerpc_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
/usr/bin/install -c .libs/libsf_dcerpc_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0 || { rm -f libsf_dcerpc_preproc.so.0 && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so || { rm -f libsf_dcerpc_preproc.so && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dcerpc_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la
/usr/bin/install -c .libs/libsf_dcerpc_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
Making all in dns
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dns_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
/usr/bin/install -c .libs/libsf_dns_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0 || { rm -f libsf_dns_preproc.so.0 && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so || { rm -f libsf_dns_preproc.so && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dns_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la
/usr/bin/install -c .libs/libsf_dns_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
Making all in ssl
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssl_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
/usr/bin/install -c .libs/libsf_ssl_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0 || { rm -f libsf_ssl_preproc.so.0 && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so || { rm -f libsf_ssl_preproc.so && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssl_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la
/usr/bin/install -c .libs/libsf_ssl_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
Making all in dcerpc2
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dce2_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
/usr/bin/install -c .libs/libsf_dce2_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0 || { rm -f libsf_dce2_preproc.so.0 && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so || { rm -f libsf_dce2_preproc.so && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dce2_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la
/usr/bin/install -c .libs/libsf_dce2_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making all in target-based
make[3]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Entering directory `/tmp/snort-2.8.5/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src'
make[2]: Leaving directory `/tmp/snort-2.8.5/src'
Making all in doc
make[2]: Entering directory `/tmp/snort-2.8.5/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/doc'
Making all in etc
make[2]: Entering directory `/tmp/snort-2.8.5/etc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/etc'
Making all in templates
make[2]: Entering directory `/tmp/snort-2.8.5/templates'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/templates'
Making all in contrib
make[2]: Entering directory `/tmp/snort-2.8.5/contrib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/contrib'
Making all in schemas
make[2]: Entering directory `/tmp/snort-2.8.5/schemas'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/schemas'
Making all in rpm
make[2]: Entering directory `/tmp/snort-2.8.5/rpm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/rpm'
Making all in m4
make[2]: Entering directory `/tmp/snort-2.8.5/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/m4'
Making all in preproc_rules
make[2]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Entering directory `/tmp/snort-2.8.5'
make[2]: Leaving directory `/tmp/snort-2.8.5'
make[1]: Leaving directory `/tmp/snort-2.8.5'
Making install in src
make[1]: Entering directory `/tmp/snort-2.8.5/src'
Making install in sfutil
make[2]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[3]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
Making install in win32
make[2]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[3]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/win32'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/win32'
Making install in output-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[3]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
Making install in detection-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make  install-am
make[3]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[4]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
Making install in dynamic-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making install in sf_engine
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make  install-recursive
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making install in examples
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
test -z "/usr/local/lib/snort_dynamicengine" || /bin/mkdir -p "/usr/local/lib/snort_dynamicengine"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_engine.la' '/usr/local/lib/snort_dynamicengine/libsf_engine.la'
/usr/bin/install -c .libs/libsf_engine.so.0.0.0 /usr/local/lib/snort_dynamicengine/libsf_engine.so.0.0.0
(cd /usr/local/lib/snort_dynamicengine && { ln -s -f libsf_engine.so.0.0.0 libsf_engine.so.0 || { rm -f libsf_engine.so.0 && ln -s libsf_engine.so.0.0.0 libsf_engine.so.0; }; })
(cd /usr/local/lib/snort_dynamicengine && { ln -s -f libsf_engine.so.0.0.0 libsf_engine.so || { rm -f libsf_engine.so && ln -s libsf_engine.so.0.0.0 libsf_engine.so; }; })
/usr/bin/install -c .libs/libsf_engine.lai /usr/local/lib/snort_dynamicengine/libsf_engine.la
/usr/bin/install -c .libs/libsf_engine.a /usr/local/lib/snort_dynamicengine/libsf_engine.a
chmod 644 /usr/local/lib/snort_dynamicengine/libsf_engine.a
ranlib /usr/local/lib/snort_dynamicengine/libsf_engine.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicengine
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicengine

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making install in sf_preproc_example
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making install in preprocessors
make[2]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
Making install in HttpInspect
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making install in include
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
Making install in utils
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
Making install in user_interface
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
Making install in session_inspection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
Making install in mode_inspection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
Making install in anomaly_detection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
Making install in event_output
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
Making install in server
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
Making install in client
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
Making install in normalization
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making install in Stream5
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
Making install in parser
make[2]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[3]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/parser'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/parser'
Making install in dynamic-preprocessors
make[2]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make  install-recursive
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making install in libs
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
Making install in ftptelnet
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make  install-recursive
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ftptelnet_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0 || { rm -f libsf_ftptelnet_preproc.so.0 && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so || { rm -f libsf_ftptelnet_preproc.so && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ftptelnet_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0 || { rm -f libsf_ftptelnet_preproc.so.0 && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so || { rm -f libsf_ftptelnet_preproc.so && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[7]: Nothing to be done for `install-data-am'.
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
Making install in smtp
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_smtp_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
/usr/bin/install -c .libs/libsf_smtp_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0 || { rm -f libsf_smtp_preproc.so.0 && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so || { rm -f libsf_smtp_preproc.so && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so; }; })
/usr/bin/install -c .libs/libsf_smtp_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la
/usr/bin/install -c .libs/libsf_smtp_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_smtp_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
/usr/bin/install -c .libs/libsf_smtp_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0 || { rm -f libsf_smtp_preproc.so.0 && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so || { rm -f libsf_smtp_preproc.so && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so; }; })
/usr/bin/install -c .libs/libsf_smtp_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la
/usr/bin/install -c .libs/libsf_smtp_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
Making install in ssh
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssh_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
/usr/bin/install -c .libs/libsf_ssh_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0 || { rm -f libsf_ssh_preproc.so.0 && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so || { rm -f libsf_ssh_preproc.so && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssh_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la
/usr/bin/install -c .libs/libsf_ssh_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssh_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
/usr/bin/install -c .libs/libsf_ssh_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0 || { rm -f libsf_ssh_preproc.so.0 && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so || { rm -f libsf_ssh_preproc.so && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssh_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la
/usr/bin/install -c .libs/libsf_ssh_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
Making install in dcerpc
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dcerpc_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
/usr/bin/install -c .libs/libsf_dcerpc_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0 || { rm -f libsf_dcerpc_preproc.so.0 && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so || { rm -f libsf_dcerpc_preproc.so && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dcerpc_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la
/usr/bin/install -c .libs/libsf_dcerpc_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dcerpc_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
/usr/bin/install -c .libs/libsf_dcerpc_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0 || { rm -f libsf_dcerpc_preproc.so.0 && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so || { rm -f libsf_dcerpc_preproc.so && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dcerpc_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la
/usr/bin/install -c .libs/libsf_dcerpc_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
Making install in dns
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dns_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
/usr/bin/install -c .libs/libsf_dns_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0 || { rm -f libsf_dns_preproc.so.0 && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so || { rm -f libsf_dns_preproc.so && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dns_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la
/usr/bin/install -c .libs/libsf_dns_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dns_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
/usr/bin/install -c .libs/libsf_dns_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0 || { rm -f libsf_dns_preproc.so.0 && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so || { rm -f libsf_dns_preproc.so && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dns_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la
/usr/bin/install -c .libs/libsf_dns_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
Making install in ssl
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssl_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
/usr/bin/install -c .libs/libsf_ssl_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0 || { rm -f libsf_ssl_preproc.so.0 && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so || { rm -f libsf_ssl_preproc.so && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssl_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la
/usr/bin/install -c .libs/libsf_ssl_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssl_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
/usr/bin/install -c .libs/libsf_ssl_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0 || { rm -f libsf_ssl_preproc.so.0 && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so || { rm -f libsf_ssl_preproc.so && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssl_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la
/usr/bin/install -c .libs/libsf_ssl_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
Making install in dcerpc2
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dce2_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
/usr/bin/install -c .libs/libsf_dce2_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0 || { rm -f libsf_dce2_preproc.so.0 && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so || { rm -f libsf_dce2_preproc.so && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dce2_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la
/usr/bin/install -c .libs/libsf_dce2_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dce2_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
/usr/bin/install -c .libs/libsf_dce2_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0 || { rm -f libsf_dce2_preproc.so.0 && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so || { rm -f libsf_dce2_preproc.so && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dce2_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la
/usr/bin/install -c .libs/libsf_dce2_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making install in target-based
make[2]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[2]: Entering directory `/tmp/snort-2.8.5/src'
make[3]: Entering directory `/tmp/snort-2.8.5/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'snort' '/usr/local/bin/snort'
/usr/bin/install -c snort /usr/local/bin/snort
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src'
make[2]: Leaving directory `/tmp/snort-2.8.5/src'
make[1]: Leaving directory `/tmp/snort-2.8.5/src'
Making install in doc
make[1]: Entering directory `/tmp/snort-2.8.5/doc'
make[2]: Entering directory `/tmp/snort-2.8.5/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/snort" || /bin/mkdir -p "/usr/local/share/doc/snort"
 /usr/bin/install -c -m 644 'AUTHORS' '/usr/local/share/doc/snort/AUTHORS'
 /usr/bin/install -c -m 644 'BUGS' '/usr/local/share/doc/snort/BUGS'
 /usr/bin/install -c -m 644 'CREDITS' '/usr/local/share/doc/snort/CREDITS'
 /usr/bin/install -c -m 644 'generators' '/usr/local/share/doc/snort/generators'
 /usr/bin/install -c -m 644 'INSTALL' '/usr/local/share/doc/snort/INSTALL'
 /usr/bin/install -c -m 644 'NEWS' '/usr/local/share/doc/snort/NEWS'
 /usr/bin/install -c -m 644 'PROBLEMS' '/usr/local/share/doc/snort/PROBLEMS'
 /usr/bin/install -c -m 644 'README' '/usr/local/share/doc/snort/README'
 /usr/bin/install -c -m 644 'README.alert_order' '/usr/local/share/doc/snort/README.alert_order'
 /usr/bin/install -c -m 644 'README.ARUBA' '/usr/local/share/doc/snort/README.ARUBA'
 /usr/bin/install -c -m 644 'README.asn1' '/usr/local/share/doc/snort/README.asn1'
 /usr/bin/install -c -m 644 'README.csv' '/usr/local/share/doc/snort/README.csv'
 /usr/bin/install -c -m 644 'README.database' '/usr/local/share/doc/snort/README.database'
 /usr/bin/install -c -m 644 'README.dcerpc' '/usr/local/share/doc/snort/README.dcerpc'
 /usr/bin/install -c -m 644 'README.dcerpc2' '/usr/local/share/doc/snort/README.dcerpc2'
 /usr/bin/install -c -m 644 'README.decode' '/usr/local/share/doc/snort/README.decode'
 /usr/bin/install -c -m 644 'README.decoder_preproc_rules' '/usr/local/share/doc/snort/README.decoder_preproc_rules'
 /usr/bin/install -c -m 644 'README.dns' '/usr/local/share/doc/snort/README.dns'
 /usr/bin/install -c -m 644 'README.event_queue' '/usr/local/share/doc/snort/README.event_queue'
 /usr/bin/install -c -m 644 'README.filters' '/usr/local/share/doc/snort/README.filters'
 /usr/bin/install -c -m 644 'README.FLEXRESP' '/usr/local/share/doc/snort/README.FLEXRESP'
 /usr/bin/install -c -m 644 'README.FLEXRESP2' '/usr/local/share/doc/snort/README.FLEXRESP2'
 /usr/bin/install -c -m 644 'README.flowbits' '/usr/local/share/doc/snort/README.flowbits'
 /usr/bin/install -c -m 644 'README.frag3' '/usr/local/share/doc/snort/README.frag3'
 /usr/bin/install -c -m 644 'README.ftptelnet' '/usr/local/share/doc/snort/README.ftptelnet'
 /usr/bin/install -c -m 644 'README.gre' '/usr/local/share/doc/snort/README.gre'
 /usr/bin/install -c -m 644 'README.http_inspect' '/usr/local/share/doc/snort/README.http_inspect'
 /usr/bin/install -c -m 644 'README.INLINE' '/usr/local/share/doc/snort/README.INLINE'
 /usr/bin/install -c -m 644 'README.ipip' '/usr/local/share/doc/snort/README.ipip'
 /usr/bin/install -c -m 644 'README.ipv6' '/usr/local/share/doc/snort/README.ipv6'
 /usr/bin/install -c -m 644 'README.multipleconfigs' '/usr/local/share/doc/snort/README.multipleconfigs'
 /usr/bin/install -c -m 644 'README.pcap_readmode' '/usr/local/share/doc/snort/README.pcap_readmode'
 /usr/bin/install -c -m 644 'README.PerfProfiling' '/usr/local/share/doc/snort/README.PerfProfiling'
 /usr/bin/install -c -m 644 'README.PLUGINS' '/usr/local/share/doc/snort/README.PLUGINS'
 /usr/bin/install -c -m 644 'README.ppm' '/usr/local/share/doc/snort/README.ppm'
 /usr/bin/install -c -m 644 'README.reload' '/usr/local/share/doc/snort/README.reload'
 /usr/bin/install -c -m 644 'README.sfportscan' '/usr/local/share/doc/snort/README.sfportscan'
 /usr/bin/install -c -m 644 'README.SMTP' '/usr/local/share/doc/snort/README.SMTP'
 /usr/bin/install -c -m 644 'README.ssh' '/usr/local/share/doc/snort/README.ssh'
 /usr/bin/install -c -m 644 'README.ssl' '/usr/local/share/doc/snort/README.ssl'
 /usr/bin/install -c -m 644 'README.stream5' '/usr/local/share/doc/snort/README.stream5'
 /usr/bin/install -c -m 644 'README.tag' '/usr/local/share/doc/snort/README.tag'
 /usr/bin/install -c -m 644 'README.thresholding' '/usr/local/share/doc/snort/README.thresholding'
 /usr/bin/install -c -m 644 'README.UNSOCK' '/usr/local/share/doc/snort/README.UNSOCK'
 /usr/bin/install -c -m 644 'README.variables' '/usr/local/share/doc/snort/README.variables'
 /usr/bin/install -c -m 644 'README.WIN32' '/usr/local/share/doc/snort/README.WIN32'
 /usr/bin/install -c -m 644 'README.wireless' '/usr/local/share/doc/snort/README.wireless'
 /usr/bin/install -c -m 644 'TODO' '/usr/local/share/doc/snort/TODO'
 /usr/bin/install -c -m 644 'USAGE' '/usr/local/share/doc/snort/USAGE'
 /usr/bin/install -c -m 644 'WISHLIST' '/usr/local/share/doc/snort/WISHLIST'
make[2]: Leaving directory `/tmp/snort-2.8.5/doc'
make[1]: Leaving directory `/tmp/snort-2.8.5/doc'
Making install in etc
make[1]: Entering directory `/tmp/snort-2.8.5/etc'
make[2]: Entering directory `/tmp/snort-2.8.5/etc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/etc'
make[1]: Leaving directory `/tmp/snort-2.8.5/etc'
Making install in templates
make[1]: Entering directory `/tmp/snort-2.8.5/templates'
make[2]: Entering directory `/tmp/snort-2.8.5/templates'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/templates'
make[1]: Leaving directory `/tmp/snort-2.8.5/templates'
Making install in contrib
make[1]: Entering directory `/tmp/snort-2.8.5/contrib'
make[2]: Entering directory `/tmp/snort-2.8.5/contrib'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/contrib'
make[1]: Leaving directory `/tmp/snort-2.8.5/contrib'
Making install in schemas
make[1]: Entering directory `/tmp/snort-2.8.5/schemas'
make[2]: Entering directory `/tmp/snort-2.8.5/schemas'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/schemas'
make[1]: Leaving directory `/tmp/snort-2.8.5/schemas'
Making install in rpm
make[1]: Entering directory `/tmp/snort-2.8.5/rpm'
make[2]: Entering directory `/tmp/snort-2.8.5/rpm'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/rpm'
make[1]: Leaving directory `/tmp/snort-2.8.5/rpm'
Making install in m4
make[1]: Entering directory `/tmp/snort-2.8.5/m4'
make[2]: Entering directory `/tmp/snort-2.8.5/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/m4'
make[1]: Leaving directory `/tmp/snort-2.8.5/m4'
Making install in preproc_rules
make[1]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[1]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[1]: Entering directory `/tmp/snort-2.8.5'
make[2]: Entering directory `/tmp/snort-2.8.5'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 './snort.8' '/usr/local/share/man/man8/snort.8'
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'snort.pc' '/usr/local/lib/pkgconfig/snort.pc'
make[2]: Leaving directory `/tmp/snort-2.8.5'
make[1]: Leaving directory `/tmp/snort-2.8.5'
```

---

### Post by Sarmacid on 2009-09-24
Did you uninstall before compiling again?

try```
make uninstall
```

Then compile it again and try to run it, post results.

---

### Post by bprof on 2009-09-24
I sure did (before not this time) but here are the newest uninstall and install. Thanks for your help.

Uninstall

```
**# make uninstall**
Making uninstall in src
make[1]: Entering directory `/tmp/snort-2.8.5/src'
Making uninstall in sfutil
make[2]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
Making uninstall in win32
make[2]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/snort-2.8.5/src/win32'
Making uninstall in output-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
Making uninstall in detection-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
Making uninstall in dynamic-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making uninstall in sf_engine
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making uninstall in examples
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicengine/libsf_engine.la'
rm -f /usr/local/lib/snort_dynamicengine/libsf_engine.la /usr/local/lib/snort_dynamicengine/libsf_engine.so.0.0.0 /usr/local/lib/snort_dynamicengine/libsf_engine.so.0 /usr/local/lib/snort_dynamicengine/libsf_engine.so /usr/local/lib/snort_dynamicengine/libsf_engine.a
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making uninstall in sf_preproc_example
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[3]: Nothing to be done for `uninstall'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[3]: Nothing to be done for `uninstall-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making uninstall in preprocessors
make[2]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
Making uninstall in HttpInspect
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making uninstall in include
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
Making uninstall in utils
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
Making uninstall in user_interface
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
Making uninstall in session_inspection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
Making uninstall in mode_inspection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
Making uninstall in anomaly_detection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
Making uninstall in event_output
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
Making uninstall in server
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
Making uninstall in client
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
Making uninstall in normalization
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[4]: Nothing to be done for `uninstall'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[4]: Nothing to be done for `uninstall-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making uninstall in Stream5
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[3]: Nothing to be done for `uninstall'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[3]: Nothing to be done for `uninstall-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
Making uninstall in parser
make[2]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/snort-2.8.5/src/parser'
Making uninstall in dynamic-preprocessors
make[2]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making uninstall in libs
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[3]: Nothing to be done for `uninstall'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
Making uninstall in ftptelnet
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
Making uninstall in smtp
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
Making uninstall in ssh
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
Making uninstall in dcerpc
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
Making uninstall in dns
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
Making uninstall in ssl
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
Making uninstall in dcerpc2
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
 /bin/bash ../../../libtool --mode=uninstall rm -f '/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
rm -f /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making uninstall in target-based
make[2]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[2]: Entering directory `/tmp/snort-2.8.5/src'
 rm -f '/usr/local/bin/snort'
make[2]: Leaving directory `/tmp/snort-2.8.5/src'
make[1]: Leaving directory `/tmp/snort-2.8.5/src'
Making uninstall in doc
make[1]: Entering directory `/tmp/snort-2.8.5/doc'
 rm -f '/usr/local/share/doc/snort/AUTHORS'
 rm -f '/usr/local/share/doc/snort/BUGS'
 rm -f '/usr/local/share/doc/snort/CREDITS'
 rm -f '/usr/local/share/doc/snort/generators'
 rm -f '/usr/local/share/doc/snort/INSTALL'
 rm -f '/usr/local/share/doc/snort/NEWS'
 rm -f '/usr/local/share/doc/snort/PROBLEMS'
 rm -f '/usr/local/share/doc/snort/README'
 rm -f '/usr/local/share/doc/snort/README.alert_order'
 rm -f '/usr/local/share/doc/snort/README.ARUBA'
 rm -f '/usr/local/share/doc/snort/README.asn1'
 rm -f '/usr/local/share/doc/snort/README.csv'
 rm -f '/usr/local/share/doc/snort/README.database'
 rm -f '/usr/local/share/doc/snort/README.dcerpc'
 rm -f '/usr/local/share/doc/snort/README.dcerpc2'
 rm -f '/usr/local/share/doc/snort/README.decode'
 rm -f '/usr/local/share/doc/snort/README.decoder_preproc_rules'
 rm -f '/usr/local/share/doc/snort/README.dns'
 rm -f '/usr/local/share/doc/snort/README.event_queue'
 rm -f '/usr/local/share/doc/snort/README.filters'
 rm -f '/usr/local/share/doc/snort/README.FLEXRESP'
 rm -f '/usr/local/share/doc/snort/README.FLEXRESP2'
 rm -f '/usr/local/share/doc/snort/README.flowbits'
 rm -f '/usr/local/share/doc/snort/README.frag3'
 rm -f '/usr/local/share/doc/snort/README.ftptelnet'
 rm -f '/usr/local/share/doc/snort/README.gre'
 rm -f '/usr/local/share/doc/snort/README.http_inspect'
 rm -f '/usr/local/share/doc/snort/README.INLINE'
 rm -f '/usr/local/share/doc/snort/README.ipip'
 rm -f '/usr/local/share/doc/snort/README.ipv6'
 rm -f '/usr/local/share/doc/snort/README.multipleconfigs'
 rm -f '/usr/local/share/doc/snort/README.pcap_readmode'
 rm -f '/usr/local/share/doc/snort/README.PerfProfiling'
 rm -f '/usr/local/share/doc/snort/README.PLUGINS'
 rm -f '/usr/local/share/doc/snort/README.ppm'
 rm -f '/usr/local/share/doc/snort/README.reload'
 rm -f '/usr/local/share/doc/snort/README.sfportscan'
 rm -f '/usr/local/share/doc/snort/README.SMTP'
 rm -f '/usr/local/share/doc/snort/README.ssh'
 rm -f '/usr/local/share/doc/snort/README.ssl'
 rm -f '/usr/local/share/doc/snort/README.stream5'
 rm -f '/usr/local/share/doc/snort/README.tag'
 rm -f '/usr/local/share/doc/snort/README.thresholding'
 rm -f '/usr/local/share/doc/snort/README.UNSOCK'
 rm -f '/usr/local/share/doc/snort/README.variables'
 rm -f '/usr/local/share/doc/snort/README.WIN32'
 rm -f '/usr/local/share/doc/snort/README.wireless'
 rm -f '/usr/local/share/doc/snort/TODO'
 rm -f '/usr/local/share/doc/snort/USAGE'
 rm -f '/usr/local/share/doc/snort/WISHLIST'
make[1]: Leaving directory `/tmp/snort-2.8.5/doc'
Making uninstall in etc
make[1]: Entering directory `/tmp/snort-2.8.5/etc'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/etc'
Making uninstall in templates
make[1]: Entering directory `/tmp/snort-2.8.5/templates'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/templates'
Making uninstall in contrib
make[1]: Entering directory `/tmp/snort-2.8.5/contrib'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/contrib'
Making uninstall in schemas
make[1]: Entering directory `/tmp/snort-2.8.5/schemas'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/schemas'
Making uninstall in rpm
make[1]: Entering directory `/tmp/snort-2.8.5/rpm'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/rpm'
Making uninstall in m4
make[1]: Entering directory `/tmp/snort-2.8.5/m4'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/m4'
Making uninstall in preproc_rules
make[1]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[1]: Nothing to be done for `uninstall'.
make[1]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[1]: Entering directory `/tmp/snort-2.8.5'
 rm -f '/usr/local/share/man/man8/snort.8'
 rm -f '/usr/local/lib/pkgconfig/snort.pc'
make[1]: Leaving directory `/tmp/snort-2.8.5'
```

Reinstall

```
# ./configure -enable-dynamicplugin --with-mysql && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dependency style of g++... none
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ranlib... (cached) ranlib
checking whether byte ordering is bigendian... no
checking for bison... bison
checking for flex... flex
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for inttypes.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for floor in -lm... yes
checking for ceil in -lm... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking whether printf must be declared... no
checking whether fprintf must be declared... no
checking whether syslog must be declared... no
checking whether puts must be declared... no
checking whether fputs must be declared... no
checking whether fputc must be declared... no
checking whether fopen must be declared... no
checking whether fclose must be declared... no
checking whether fwrite must be declared... no
checking whether fflush must be declared... no
checking whether getopt must be declared... no
checking whether bzero must be declared... no
checking whether bcopy must be declared... no
checking whether memset must be declared... no
checking whether strtol must be declared... no
checking whether strcasecmp must be declared... no
checking whether strncasecmp must be declared... no
checking whether strerror must be declared... no
checking whether perror must be declared... no
checking whether socket must be declared... no
checking whether sendto must be declared... no
checking whether vsnprintf must be declared... no
checking whether snprintf must be declared... no
checking whether strtoul must be declared... no
checking for snprintf... yes
checking for strlcpy... no
checking for strlcat... no
checking for strerror... yes
checking for vswprintf... yes
checking for wprintf... yes
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long int... yes
checking size of long int... 4
checking for long long int... yes
checking size of long long int... 8
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long int... yes
checking size of unsigned long int... 4
checking for unsigned long long int... yes
checking size of unsigned long long int... 8
checking for u_int8_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for u_int64_t... yes
checking for uint8_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for int8_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for INADDR_NONE... yes
checking for __FUNCTION__... yes
checking for pcap_datalink in -lpcap... yes
checking for libpcap version >= 0.9... yes
checking for libpcap version 0.9.0 - 0.9.4... no
checking pcre.h usability... yes
checking pcre.h presence... yes
checking for pcre.h... yes
checking for pcre_compile in -lpcre... yes
checking for libpcre version 6.0 or greater... yes
checking for sparc... no
checking for visibility support... yes
checking for dlsym in -ldl... yes
checking for mysql... yes
checking for compress in -lz... yes
checking for mysql default client reconnect... no
checking for mysql reconnect option... yes
checking for mysql setting of reconnect option before connect bug... no
checking for linuxthreads... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating snort.pc
config.status: WARNING:  snort.pc.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/sfutil/Makefile
config.status: creating src/detection-plugins/Makefile
config.status: creating src/dynamic-plugins/Makefile
config.status: creating src/dynamic-plugins/sf_engine/Makefile
config.status: creating src/dynamic-plugins/sf_engine/examples/Makefile
config.status: creating src/dynamic-plugins/sf_preproc_example/Makefile
config.status: creating src/dynamic-preprocessors/Makefile
config.status: creating src/dynamic-preprocessors/libs/Makefile
config.status: creating src/dynamic-preprocessors/ftptelnet/Makefile
config.status: creating src/dynamic-preprocessors/smtp/Makefile
config.status: creating src/dynamic-preprocessors/ssh/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc2/Makefile
config.status: creating src/dynamic-preprocessors/dns/Makefile
config.status: creating src/dynamic-preprocessors/ssl/Makefile
config.status: creating src/output-plugins/Makefile
config.status: creating src/preprocessors/Makefile
config.status: creating src/preprocessors/HttpInspect/Makefile
config.status: creating src/preprocessors/HttpInspect/include/Makefile
config.status: creating src/preprocessors/HttpInspect/utils/Makefile
config.status: creating src/preprocessors/HttpInspect/anomaly_detection/Makefile
config.status: creating src/preprocessors/HttpInspect/client/Makefile
config.status: creating src/preprocessors/HttpInspect/event_output/Makefile
config.status: creating src/preprocessors/HttpInspect/mode_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/normalization/Makefile
config.status: creating src/preprocessors/HttpInspect/server/Makefile
config.status: creating src/preprocessors/HttpInspect/session_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/user_interface/Makefile
config.status: creating src/preprocessors/Stream5/Makefile
config.status: creating src/parser/Makefile
config.status: creating src/target-based/Makefile
config.status: creating doc/Makefile
config.status: creating contrib/Makefile
config.status: creating schemas/Makefile
config.status: creating rpm/Makefile
config.status: creating preproc_rules/Makefile
config.status: creating m4/Makefile
config.status: creating etc/Makefile
config.status: creating templates/Makefile
config.status: creating src/win32/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/tmp/snort-2.8.5'
Making all in src
make[2]: Entering directory `/tmp/snort-2.8.5/src'
Making all in sfutil
make[3]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
Making all in win32
make[3]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/win32'
Making all in output-plugins
make[3]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
Making all in detection-plugins
make[3]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make  all-am
make[4]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
Making all in dynamic-plugins
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making all in sf_engine
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make  all-recursive
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making all in examples
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making all in sf_preproc_example
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making all in preprocessors
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
Making all in HttpInspect
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making all in include
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
Making all in utils
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
Making all in user_interface
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
Making all in session_inspection
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
Making all in mode_inspection
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
Making all in anomaly_detection
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
Making all in event_output
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
Making all in server
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
Making all in client
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
Making all in normalization
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making all in Stream5
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
Making all in parser
make[3]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/parser'
Making all in dynamic-preprocessors
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make  all-recursive
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making all in libs
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
Making all in ftptelnet
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make  all-recursive
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[8]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ftptelnet_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0 || { rm -f libsf_ftptelnet_preproc.so.0 && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so || { rm -f libsf_ftptelnet_preproc.so && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[8]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
Making all in smtp
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_smtp_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
/usr/bin/install -c .libs/libsf_smtp_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0 || { rm -f libsf_smtp_preproc.so.0 && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so || { rm -f libsf_smtp_preproc.so && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so; }; })
/usr/bin/install -c .libs/libsf_smtp_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la
/usr/bin/install -c .libs/libsf_smtp_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
Making all in ssh
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssh_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
/usr/bin/install -c .libs/libsf_ssh_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0 || { rm -f libsf_ssh_preproc.so.0 && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so || { rm -f libsf_ssh_preproc.so && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssh_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la
/usr/bin/install -c .libs/libsf_ssh_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
Making all in dcerpc
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dcerpc_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
/usr/bin/install -c .libs/libsf_dcerpc_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0 || { rm -f libsf_dcerpc_preproc.so.0 && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so || { rm -f libsf_dcerpc_preproc.so && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dcerpc_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la
/usr/bin/install -c .libs/libsf_dcerpc_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
Making all in dns
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dns_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
/usr/bin/install -c .libs/libsf_dns_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0 || { rm -f libsf_dns_preproc.so.0 && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so || { rm -f libsf_dns_preproc.so && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dns_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la
/usr/bin/install -c .libs/libsf_dns_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
Making all in ssl
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssl_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
/usr/bin/install -c .libs/libsf_ssl_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0 || { rm -f libsf_ssl_preproc.so.0 && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so || { rm -f libsf_ssl_preproc.so && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssl_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la
/usr/bin/install -c .libs/libsf_ssl_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
Making all in dcerpc2
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make  all-am
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dce2_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
/usr/bin/install -c .libs/libsf_dce2_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0 || { rm -f libsf_dce2_preproc.so.0 && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so || { rm -f libsf_dce2_preproc.so && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dce2_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la
/usr/bin/install -c .libs/libsf_dce2_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making all in target-based
make[3]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Entering directory `/tmp/snort-2.8.5/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src'
make[2]: Leaving directory `/tmp/snort-2.8.5/src'
Making all in doc
make[2]: Entering directory `/tmp/snort-2.8.5/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/doc'
Making all in etc
make[2]: Entering directory `/tmp/snort-2.8.5/etc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/etc'
Making all in templates
make[2]: Entering directory `/tmp/snort-2.8.5/templates'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/templates'
Making all in contrib
make[2]: Entering directory `/tmp/snort-2.8.5/contrib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/contrib'
Making all in schemas
make[2]: Entering directory `/tmp/snort-2.8.5/schemas'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/schemas'
Making all in rpm
make[2]: Entering directory `/tmp/snort-2.8.5/rpm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/rpm'
Making all in m4
make[2]: Entering directory `/tmp/snort-2.8.5/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/m4'
Making all in preproc_rules
make[2]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Entering directory `/tmp/snort-2.8.5'
make[2]: Leaving directory `/tmp/snort-2.8.5'
make[1]: Leaving directory `/tmp/snort-2.8.5'
Making install in src
make[1]: Entering directory `/tmp/snort-2.8.5/src'
Making install in sfutil
make[2]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[3]: Entering directory `/tmp/snort-2.8.5/src/sfutil'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/sfutil'
Making install in win32
make[2]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[3]: Entering directory `/tmp/snort-2.8.5/src/win32'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/win32'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/win32'
Making install in output-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[3]: Entering directory `/tmp/snort-2.8.5/src/output-plugins'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/output-plugins'
Making install in detection-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make  install-am
make[3]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[4]: Entering directory `/tmp/snort-2.8.5/src/detection-plugins'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/detection-plugins'
Making install in dynamic-plugins
make[2]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making install in sf_engine
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make  install-recursive
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making install in examples
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine/examples'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
test -z "/usr/local/lib/snort_dynamicengine" || /bin/mkdir -p "/usr/local/lib/snort_dynamicengine"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_engine.la' '/usr/local/lib/snort_dynamicengine/libsf_engine.la'
/usr/bin/install -c .libs/libsf_engine.so.0.0.0 /usr/local/lib/snort_dynamicengine/libsf_engine.so.0.0.0
(cd /usr/local/lib/snort_dynamicengine && { ln -s -f libsf_engine.so.0.0.0 libsf_engine.so.0 || { rm -f libsf_engine.so.0 && ln -s libsf_engine.so.0.0.0 libsf_engine.so.0; }; })
(cd /usr/local/lib/snort_dynamicengine && { ln -s -f libsf_engine.so.0.0.0 libsf_engine.so || { rm -f libsf_engine.so && ln -s libsf_engine.so.0.0.0 libsf_engine.so; }; })
/usr/bin/install -c .libs/libsf_engine.lai /usr/local/lib/snort_dynamicengine/libsf_engine.la
/usr/bin/install -c .libs/libsf_engine.a /usr/local/lib/snort_dynamicengine/libsf_engine.a
chmod 644 /usr/local/lib/snort_dynamicengine/libsf_engine.a
ranlib /usr/local/lib/snort_dynamicengine/libsf_engine.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicengine
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicengine

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_engine'
Making install in sf_preproc_example
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins/sf_preproc_example'
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-plugins'
Making install in preprocessors
make[2]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
Making install in HttpInspect
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making install in include
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/include'
Making install in utils
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/utils'
Making install in user_interface
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/user_interface'
Making install in session_inspection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/session_inspection'
Making install in mode_inspection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/mode_inspection'
Making install in anomaly_detection
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/anomaly_detection'
Making install in event_output
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/event_output'
Making install in server
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/server'
Making install in client
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/client'
Making install in normalization
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect/normalization'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[5]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/HttpInspect'
Making install in Stream5
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors/Stream5'
make[3]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[4]: Entering directory `/tmp/snort-2.8.5/src/preprocessors'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/preprocessors'
Making install in parser
make[2]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[3]: Entering directory `/tmp/snort-2.8.5/src/parser'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/parser'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/parser'
Making install in dynamic-preprocessors
make[2]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make  install-recursive
make[3]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making install in libs
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/libs'
Making install in ftptelnet
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make  install-recursive
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ftptelnet_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0 || { rm -f libsf_ftptelnet_preproc.so.0 && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so || { rm -f libsf_ftptelnet_preproc.so && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[7]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ftptelnet_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la'
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0 || { rm -f libsf_ftptelnet_preproc.so.0 && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so || { rm -f libsf_ftptelnet_preproc.so && ln -s libsf_ftptelnet_preproc.so.0.0.0 libsf_ftptelnet_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.la
/usr/bin/install -c .libs/libsf_ftptelnet_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[7]: Nothing to be done for `install-data-am'.
make[7]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ftptelnet'
Making install in smtp
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_smtp_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
/usr/bin/install -c .libs/libsf_smtp_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0 || { rm -f libsf_smtp_preproc.so.0 && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so || { rm -f libsf_smtp_preproc.so && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so; }; })
/usr/bin/install -c .libs/libsf_smtp_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la
/usr/bin/install -c .libs/libsf_smtp_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/smtp/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_smtp_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la'
/usr/bin/install -c .libs/libsf_smtp_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0 || { rm -f libsf_smtp_preproc.so.0 && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so || { rm -f libsf_smtp_preproc.so && ln -s libsf_smtp_preproc.so.0.0.0 libsf_smtp_preproc.so; }; })
/usr/bin/install -c .libs/libsf_smtp_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.la
/usr/bin/install -c .libs/libsf_smtp_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/smtp'
Making install in ssh
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssh_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
/usr/bin/install -c .libs/libsf_ssh_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0 || { rm -f libsf_ssh_preproc.so.0 && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so || { rm -f libsf_ssh_preproc.so && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssh_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la
/usr/bin/install -c .libs/libsf_ssh_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssh/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssh_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la'
/usr/bin/install -c .libs/libsf_ssh_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0 || { rm -f libsf_ssh_preproc.so.0 && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so || { rm -f libsf_ssh_preproc.so && ln -s libsf_ssh_preproc.so.0.0.0 libsf_ssh_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssh_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.la
/usr/bin/install -c .libs/libsf_ssh_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssh'
Making install in dcerpc
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dcerpc_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
/usr/bin/install -c .libs/libsf_dcerpc_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0 || { rm -f libsf_dcerpc_preproc.so.0 && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so || { rm -f libsf_dcerpc_preproc.so && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dcerpc_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la
/usr/bin/install -c .libs/libsf_dcerpc_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dcerpc_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la'
/usr/bin/install -c .libs/libsf_dcerpc_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0 || { rm -f libsf_dcerpc_preproc.so.0 && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so || { rm -f libsf_dcerpc_preproc.so && ln -s libsf_dcerpc_preproc.so.0.0.0 libsf_dcerpc_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dcerpc_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.la
/usr/bin/install -c .libs/libsf_dcerpc_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc'
Making install in dns
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dns_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
/usr/bin/install -c .libs/libsf_dns_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0 || { rm -f libsf_dns_preproc.so.0 && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so || { rm -f libsf_dns_preproc.so && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dns_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la
/usr/bin/install -c .libs/libsf_dns_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dns/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dns_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la'
/usr/bin/install -c .libs/libsf_dns_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0 || { rm -f libsf_dns_preproc.so.0 && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so || { rm -f libsf_dns_preproc.so && ln -s libsf_dns_preproc.so.0.0.0 libsf_dns_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dns_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.la
/usr/bin/install -c .libs/libsf_dns_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dns'
Making install in ssl
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssl_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
/usr/bin/install -c .libs/libsf_ssl_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0 || { rm -f libsf_ssl_preproc.so.0 && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so || { rm -f libsf_ssl_preproc.so && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssl_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la
/usr/bin/install -c .libs/libsf_ssl_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/ssl/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_ssl_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la'
/usr/bin/install -c .libs/libsf_ssl_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0 || { rm -f libsf_ssl_preproc.so.0 && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so || { rm -f libsf_ssl_preproc.so && ln -s libsf_ssl_preproc.so.0.0.0 libsf_ssl_preproc.so; }; })
/usr/bin/install -c .libs/libsf_ssl_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.la
/usr/bin/install -c .libs/libsf_ssl_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/ssl'
Making install in dcerpc2
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make  install-am
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make DESTDIR=`pwd`/../build install-libLTLIBRARIES
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dce2_preproc.la' '/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
/usr/bin/install -c .libs/libsf_dce2_preproc.so.0.0.0 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0 || { rm -f libsf_dce2_preproc.so.0 && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0; }; })
(cd /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so || { rm -f libsf_dce2_preproc.so && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dce2_preproc.lai /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la
/usr/bin/install -c .libs/libsf_dce2_preproc.a /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
chmod 644 /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
ranlib /tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2/../build/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
libtool: install: warning: remember to run `libtool --finish /usr/local/lib/snort_dynamicpreprocessor'
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[6]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
test -z "/usr/local/lib/snort_dynamicpreprocessor" || /bin/mkdir -p "/usr/local/lib/snort_dynamicpreprocessor"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libsf_dce2_preproc.la' '/usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la'
/usr/bin/install -c .libs/libsf_dce2_preproc.so.0.0.0 /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so.0.0.0
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0 || { rm -f libsf_dce2_preproc.so.0 && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so.0; }; })
(cd /usr/local/lib/snort_dynamicpreprocessor && { ln -s -f libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so || { rm -f libsf_dce2_preproc.so && ln -s libsf_dce2_preproc.so.0.0.0 libsf_dce2_preproc.so; }; })
/usr/bin/install -c .libs/libsf_dce2_preproc.lai /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.la
/usr/bin/install -c .libs/libsf_dce2_preproc.a /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
chmod 644 /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
ranlib /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/snort_dynamicpreprocessor
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/snort_dynamicpreprocessor

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
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors/dcerpc2'
make[4]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[5]: Entering directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[4]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[3]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/dynamic-preprocessors'
Making install in target-based
make[2]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Entering directory `/tmp/snort-2.8.5/src/target-based'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[2]: Leaving directory `/tmp/snort-2.8.5/src/target-based'
make[2]: Entering directory `/tmp/snort-2.8.5/src'
make[3]: Entering directory `/tmp/snort-2.8.5/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'snort' '/usr/local/bin/snort'
/usr/bin/install -c snort /usr/local/bin/snort
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/tmp/snort-2.8.5/src'
make[2]: Leaving directory `/tmp/snort-2.8.5/src'
make[1]: Leaving directory `/tmp/snort-2.8.5/src'
Making install in doc
make[1]: Entering directory `/tmp/snort-2.8.5/doc'
make[2]: Entering directory `/tmp/snort-2.8.5/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/snort" || /bin/mkdir -p "/usr/local/share/doc/snort"
 /usr/bin/install -c -m 644 'AUTHORS' '/usr/local/share/doc/snort/AUTHORS'
 /usr/bin/install -c -m 644 'BUGS' '/usr/local/share/doc/snort/BUGS'
 /usr/bin/install -c -m 644 'CREDITS' '/usr/local/share/doc/snort/CREDITS'
 /usr/bin/install -c -m 644 'generators' '/usr/local/share/doc/snort/generators'
 /usr/bin/install -c -m 644 'INSTALL' '/usr/local/share/doc/snort/INSTALL'
 /usr/bin/install -c -m 644 'NEWS' '/usr/local/share/doc/snort/NEWS'
 /usr/bin/install -c -m 644 'PROBLEMS' '/usr/local/share/doc/snort/PROBLEMS'
 /usr/bin/install -c -m 644 'README' '/usr/local/share/doc/snort/README'
 /usr/bin/install -c -m 644 'README.alert_order' '/usr/local/share/doc/snort/README.alert_order'
 /usr/bin/install -c -m 644 'README.ARUBA' '/usr/local/share/doc/snort/README.ARUBA'
 /usr/bin/install -c -m 644 'README.asn1' '/usr/local/share/doc/snort/README.asn1'
 /usr/bin/install -c -m 644 'README.csv' '/usr/local/share/doc/snort/README.csv'
 /usr/bin/install -c -m 644 'README.database' '/usr/local/share/doc/snort/README.database'
 /usr/bin/install -c -m 644 'README.dcerpc' '/usr/local/share/doc/snort/README.dcerpc'
 /usr/bin/install -c -m 644 'README.dcerpc2' '/usr/local/share/doc/snort/README.dcerpc2'
 /usr/bin/install -c -m 644 'README.decode' '/usr/local/share/doc/snort/README.decode'
 /usr/bin/install -c -m 644 'README.decoder_preproc_rules' '/usr/local/share/doc/snort/README.decoder_preproc_rules'
 /usr/bin/install -c -m 644 'README.dns' '/usr/local/share/doc/snort/README.dns'
 /usr/bin/install -c -m 644 'README.event_queue' '/usr/local/share/doc/snort/README.event_queue'
 /usr/bin/install -c -m 644 'README.filters' '/usr/local/share/doc/snort/README.filters'
 /usr/bin/install -c -m 644 'README.FLEXRESP' '/usr/local/share/doc/snort/README.FLEXRESP'
 /usr/bin/install -c -m 644 'README.FLEXRESP2' '/usr/local/share/doc/snort/README.FLEXRESP2'
 /usr/bin/install -c -m 644 'README.flowbits' '/usr/local/share/doc/snort/README.flowbits'
 /usr/bin/install -c -m 644 'README.frag3' '/usr/local/share/doc/snort/README.frag3'
 /usr/bin/install -c -m 644 'README.ftptelnet' '/usr/local/share/doc/snort/README.ftptelnet'
 /usr/bin/install -c -m 644 'README.gre' '/usr/local/share/doc/snort/README.gre'
 /usr/bin/install -c -m 644 'README.http_inspect' '/usr/local/share/doc/snort/README.http_inspect'
 /usr/bin/install -c -m 644 'README.INLINE' '/usr/local/share/doc/snort/README.INLINE'
 /usr/bin/install -c -m 644 'README.ipip' '/usr/local/share/doc/snort/README.ipip'
 /usr/bin/install -c -m 644 'README.ipv6' '/usr/local/share/doc/snort/README.ipv6'
 /usr/bin/install -c -m 644 'README.multipleconfigs' '/usr/local/share/doc/snort/README.multipleconfigs'
 /usr/bin/install -c -m 644 'README.pcap_readmode' '/usr/local/share/doc/snort/README.pcap_readmode'
 /usr/bin/install -c -m 644 'README.PerfProfiling' '/usr/local/share/doc/snort/README.PerfProfiling'
 /usr/bin/install -c -m 644 'README.PLUGINS' '/usr/local/share/doc/snort/README.PLUGINS'
 /usr/bin/install -c -m 644 'README.ppm' '/usr/local/share/doc/snort/README.ppm'
 /usr/bin/install -c -m 644 'README.reload' '/usr/local/share/doc/snort/README.reload'
 /usr/bin/install -c -m 644 'README.sfportscan' '/usr/local/share/doc/snort/README.sfportscan'
 /usr/bin/install -c -m 644 'README.SMTP' '/usr/local/share/doc/snort/README.SMTP'
 /usr/bin/install -c -m 644 'README.ssh' '/usr/local/share/doc/snort/README.ssh'
 /usr/bin/install -c -m 644 'README.ssl' '/usr/local/share/doc/snort/README.ssl'
 /usr/bin/install -c -m 644 'README.stream5' '/usr/local/share/doc/snort/README.stream5'
 /usr/bin/install -c -m 644 'README.tag' '/usr/local/share/doc/snort/README.tag'
 /usr/bin/install -c -m 644 'README.thresholding' '/usr/local/share/doc/snort/README.thresholding'
 /usr/bin/install -c -m 644 'README.UNSOCK' '/usr/local/share/doc/snort/README.UNSOCK'
 /usr/bin/install -c -m 644 'README.variables' '/usr/local/share/doc/snort/README.variables'
 /usr/bin/install -c -m 644 'README.WIN32' '/usr/local/share/doc/snort/README.WIN32'
 /usr/bin/install -c -m 644 'README.wireless' '/usr/local/share/doc/snort/README.wireless'
 /usr/bin/install -c -m 644 'TODO' '/usr/local/share/doc/snort/TODO'
 /usr/bin/install -c -m 644 'USAGE' '/usr/local/share/doc/snort/USAGE'
 /usr/bin/install -c -m 644 'WISHLIST' '/usr/local/share/doc/snort/WISHLIST'
make[2]: Leaving directory `/tmp/snort-2.8.5/doc'
make[1]: Leaving directory `/tmp/snort-2.8.5/doc'
Making install in etc
make[1]: Entering directory `/tmp/snort-2.8.5/etc'
make[2]: Entering directory `/tmp/snort-2.8.5/etc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/etc'
make[1]: Leaving directory `/tmp/snort-2.8.5/etc'
Making install in templates
make[1]: Entering directory `/tmp/snort-2.8.5/templates'
make[2]: Entering directory `/tmp/snort-2.8.5/templates'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/templates'
make[1]: Leaving directory `/tmp/snort-2.8.5/templates'
Making install in contrib
make[1]: Entering directory `/tmp/snort-2.8.5/contrib'
make[2]: Entering directory `/tmp/snort-2.8.5/contrib'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/contrib'
make[1]: Leaving directory `/tmp/snort-2.8.5/contrib'
Making install in schemas
make[1]: Entering directory `/tmp/snort-2.8.5/schemas'
make[2]: Entering directory `/tmp/snort-2.8.5/schemas'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/schemas'
make[1]: Leaving directory `/tmp/snort-2.8.5/schemas'
Making install in rpm
make[1]: Entering directory `/tmp/snort-2.8.5/rpm'
make[2]: Entering directory `/tmp/snort-2.8.5/rpm'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/rpm'
make[1]: Leaving directory `/tmp/snort-2.8.5/rpm'
Making install in m4
make[1]: Entering directory `/tmp/snort-2.8.5/m4'
make[2]: Entering directory `/tmp/snort-2.8.5/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/m4'
make[1]: Leaving directory `/tmp/snort-2.8.5/m4'
Making install in preproc_rules
make[1]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Entering directory `/tmp/snort-2.8.5/preproc_rules'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[1]: Leaving directory `/tmp/snort-2.8.5/preproc_rules'
make[1]: Entering directory `/tmp/snort-2.8.5'
make[2]: Entering directory `/tmp/snort-2.8.5'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 './snort.8' '/usr/local/share/man/man8/snort.8'
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'snort.pc' '/usr/local/lib/pkgconfig/snort.pc'
make[2]: Leaving directory `/tmp/snort-2.8.5'
make[1]: Leaving directory `/tmp/snort-2.8.5'

```

The result after running snort:

```
snort -v -c /etc/snort/snort.conf 
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/etc/snort/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 80 2301 3128 7777 7779 8000 8008 8028 8080 8180 8888 9999 ]
PortVar 'SHELLCODE_PORTS' defined :  [ any ]
PortVar 'ORACLE_PORTS' defined :  [ 1024:65535 ]
PortVar 'AUTH_PORTS' defined :  [ 113 ]
PortVar 'DNS_PORTS' defined :  [ 53 ]
PortVar 'FINGER_PORTS' defined :  [ 79 ]
PortVar 'FTP_PORTS' defined :  [ 21 ]
PortVar 'IMAP_PORTS' defined :  [ 143 ]
PortVar 'IRC_PORTS' defined :  [ 6665:6669 7000 ]
PortVar 'MSSQL_PORTS' defined :  [ 1433 ]
PortVar 'NNTP_PORTS' defined :  [ 119 ]
PortVar 'POP2_PORTS' defined :  [ 109 ]
PortVar 'POP3_PORTS' defined :  [ 110 ]
PortVar 'SUNRPC_PORTS' defined :  [ 111 32770:32779 ]
PortVar 'RLOGIN_PORTS' defined :  [ 513 ]
PortVar 'RSH_PORTS' defined :  [ 514 ]
PortVar 'SMB_PORTS' defined :  [ 139 445 ]
PortVar 'SMTP_PORTS' defined :  [ 25 ]
PortVar 'SNMP_PORTS' defined :  [ 161 ]
PortVar 'SSH_PORTS' defined :  [ 22 ]
PortVar 'TELNET_PORTS' defined :  [ 23 ]
PortVar 'MAIL_PORTS' defined :  [ 25 143 465 691 ]
PortVar 'SSL_PORTS' defined :  [ 25 443 465 636 993 995 ]
PortVar 'DCERPC_NCACN_IP_TCP' defined :  [ 139 445 ]
PortVar 'DCERPC_NCADG_IP_UDP' defined :  [ 138 1024:65535 ]
PortVar 'DCERPC_NCACN_IP_LONG' defined :  [ 135 139 445 593 1024:65535 ]
PortVar 'DCERPC_NCACN_UDP_LONG' defined :  [ 135 1024:65535 ]
PortVar 'DCERPC_NCACN_UDP_SHORT' defined :  [ 135 593 1024:65535 ]
PortVar 'DCERPC_NCACN_TCP' defined :  [ 2103 2105 2107 ]
PortVar 'DCERPC_BRIGHTSTORE' defined :  [ 6503:6504 ]
Tagged Packet Limit: 256
Loading dynamic engine /usr/local/lib/snort_dynamicengine/libsf_engine.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/bad-traffic.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/chat.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/dos.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/exploit.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/imap.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/misc.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/multimedia.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/netbios.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/nntp.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/p2p.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/smtp.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/sql.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/web-client.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/web-misc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_dce2_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_ssl_preproc.so... done
Log directory = /var/log/snort
[COLOR="Red"]database: 'mysql' support is not compiled into this build of snort[/COLOR]

ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..

```

Still failing.

---

### Post by Sarmacid on 2009-09-24
Did you install MySQL from the repos?

If you didn't, try --with-mysql=DIR as indicated by the error, if not I'm out of ideas :|

---

### Post by bprof on 2009-09-24
Yes installed them from the repos. This is what I used for the install:

```
apt-get -y install build-essential libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev
```

This is what I have:

```
mysql -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 54
Server version: 5.0.75-0ubuntu10.2 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use snort;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+------------------+
| Tables_in_snort  |
+------------------+
| acid_ag          | 
| acid_ag_alert    | 
| acid_event       | 
| acid_ip_cache    | 
| base_roles       | 
| base_users       | 
| data             | 
| detail           | 
| encoding         | 
| event            | 
| icmphdr          | 
| iphdr            | 
| opt              | 
| reference        | 
| reference_system | 
| schema           | 
| sensor           | 
| sig_class        | 
| sig_reference    | 
| signature        | 
| tcphdr           | 
| udphdr           | 
+------------------+
22 rows in set (0.00 sec)

```

But I don't know what is causing this issue? :confused:

---

