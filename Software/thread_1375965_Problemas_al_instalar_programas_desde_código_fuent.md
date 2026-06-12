---
title: "Problemas al instalar programas desde código fuente"
date: 2010-01-08
forum: Software
---

### Post by asterix77 on 2010-01-08
He descargado el código fuente de un programa que quiero instalar, los pasos que sigo son los siguientes.

[LIST]
[*]Descomprimirlo en mi HOME
[/LIST]

[LIST]
[*]ingresar a la carpeta creada
[/LIST]

[LIST]
[*]Leerme el archivo README e INSTALL, para seguir las instrucciones
[/LIST]

[LIST]
[*]realizo el ./configure el cual al principio me coloca
[/LIST]
[I]./configure 
checking whether to enable maintainer-specific portions of Makefiles... no
[/I]
Luego continúa, y al final me aparece lo siguiente:

*configure: error: not found*.  Por lo que asumo que la operación se realizó con éxito


[LIST]
[*]Al realizar el make aparece:
[/LIST]
[I]make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
[/I]
Y el proceso se detiene. Les comento que tengo instalado el paquete build-essensial

Mi pregunta es entonces ¿porqué sucede este error?. ¿Falta de librerias o de dependencias del sistema operativo para realizar el proceso?

Uso ubuntu Karmic

Saludos

---

### Post by moreback on 2010-01-08
Esa línea de error en el ./configure no te la creo, tiene que haber algo más arriba que sirva para identificar el error.

Probablemente sea que te falte algún paquete de desarrollo de alguna biblioteca que necesite el programa que estas intentando compilar.

Saludos.

---

### Post by CdK1 on 2010-01-08
./configure y pega lo que sale acá...

---

### Post by asterix77 on 2010-01-09
Es un poco largo, pero esto es lo que me arroja[I] ./configure

checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking if your compiler supports __VA_ARGS__ in macro declarations... yes
checking for bison... no
checking for byacc... no
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for library containing dlopen... -ldl
checking for an ANSI C-conforming const... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib64 /usr/lib64
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for library containing lt_dlopen... no
checking for dlfcn.h... (cached) yes
checking ltdl.h usability... no
checking ltdl.h presence... no
checking for ltdl.h... no
checking whether byte ordering is bigendian... no
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for dirent.h that defines DIR... (cached) yes
checking for library containing opendir... (cached) none required
checking for unistd.h... (cached) yes
checking for stdlib.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/types.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for errno.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for ctype.h... (cached) yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking for NS_GET32... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking for size_t... yes
checking for an ANSI C-conforming const... (cached) yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for library containing pthread_create... -lpthread
checking whether gcc accepts -pthread... yes
checking for getifaddrs... yes
checking for gettimeofday... yes
checking for vsnprintf... yes
checking for select... yes
checking for poll... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes
checking for strsignal... yes
checking for strtok_r... yes
checking for uname... yes
checking for daemon... yes

Checking for required libraries...

checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing poll... none required
checking for library containing gzopen... no
configure: error: not found.



Saludos
[/I]

---

### Post by moreback on 2010-01-09
Creo que el problema está en la línea antes del error:

***checking for library containing gzopen... no***

Al parecer no encuentra ninguna biblioteca que contenga la función gzopen, por lo que creo que te falta la biblioteca de desarrollo de zlib, que aparece en Synaptic como [zlib1g-dev]("apt:zlib1g-dev").

Saludos.

---

### Post by CdK1 on 2010-01-14
Como señala moreback, necesitas las dev de* zlib, pero mi duda es, que estás tratando de compilar?*

---

### Post by jperelli on 2012-04-17
Por si alguien llega aqui con el mismo problema que yo, me pasó lo mismo compilando ettercap en cygwin.

Instalé la librería que se encuentra en
 Devel -> zlib-devel

Solucionó mi problema.

---

