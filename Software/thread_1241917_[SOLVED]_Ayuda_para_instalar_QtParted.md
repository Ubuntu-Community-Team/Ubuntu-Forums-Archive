---
title: "[SOLVED] Ayuda para instalar QtParted"
date: 2009-08-16
forum: Software
---

### Post by daggaz on 2009-08-16
Hola.
Me conseguí un disco duro de un treabyte : > para usarlo como DD externo para manejar el alacenamiento de audio y video (lo cual me ayudará a evitar que se me acaben los Gb del disco interno de la Lap unos 300Gb que se van volando con video). El caso es que el DD venía con un montón de archivos del dueño anterior que la verdad no me interesan y quería formatearlo. 
También tengo un lápiz USB de 4 Gb que no sirve de nada; intenté hacer un disco de arranque de Ubuntu y algo pasó que ni es disco de arranque ni puedo eliminar los datos que tiene (ni desde la terminal como root), y quería formatearlo, pensé que era la opción.
Debido a estos dos problemas me decidí a instalar QtParted, aparentemente la mejor opción gráfica para formatear y particionar discos en Linux. Bajé el archivo comprimido y leí el Readme, encontré que necesitaba tener instaladlo GNUparted primero.
Lo bajo y lo trato de instalar; la verdad nunca he sido muy bueno para instalar compilando, lo he hecho solo una o dos veces, pero parece que para estos dos programas necesito hacerlo. Lo intenté con GNU parted descomprimiendo manualmente la carpeta en el directorio de usuario. Luego entro a la consola (con «sudo -s») y con «cd» me cambio al directorio del programa.
Una vez ahí ejecuto el comando «./configure » (así, literalmente, sin comillas claro). Y bueno, me dio un error, instalo (según yo), lo que me provoca el error y bueno... Mejor pego el código:

```
configure: error: libdevmapper could not be found, but is required for the
--enable-device-mapper option, which is enabled by default.  Either disable
device-mapper support with --disable-device-mapper or download and install
device-mapper from:
    http://sources.redhat.com/dm/
Note: if you are using precompiled packages you will need the development
package as well (it may be called device-mapper-devel or something similar).
    
root@diego-hpcompaq:~/parted-1.9.0# apt-get install libdevmapper
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando libdevmapper1.02.1 en lugar de libdevmapper
libdevmapper1.02.1 ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
root@diego-hpcompaq:~/parted-1.9.0# ./configure; make; make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking whether gcc and cc understand -c and -o together... yes
checking for ranlib... ranlib
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for a usable (O_DIRECT-supporting) temporary dir... .
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for working alloca.h... yes
checking for alloca... yes
checking for btowc... yes
checking for __fpending... yes
checking for mbsinit... yes
checking for mbrtowc... yes
checking for mprotect... yes
checking for isblank... yes
checking for iswctype... yes
checking for wcscoll... yes
checking for wcrtomb... yes
checking for iswcntrl... yes
checking for setenv... yes
checking for wctob... yes
checking for nl_langinfo and CODESET... yes
checking for a traditional french locale... none
checking for size_t... yes
checking whether malloc, realloc, calloc are POSIX compliant... yes
checking whether system is Windows or MSDOS... no
checking whether // is distinct from /... no
checking whether the preprocessor supports include_next... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking stdio_ext.h usability... yes
checking stdio_ext.h presence... yes
checking for stdio_ext.h... yes
checking for stdint.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for inttypes.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for stdlib.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking wctype.h usability... yes
checking wctype.h presence... yes
checking for wctype.h... yes
checking for complete errno.h... yes
checking whether strerror_r is declared... yes
checking for strerror_r... yes
checking whether strerror_r returns char *... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for getopt_long_only... yes
checking whether optreset is declared... no
checking for working GNU getopt function... yes
checking whether getenv is declared... yes
checking for inline... inline
checking for long long int... yes
checking for unsigned long long int... yes
checking whether stdint.h conforms to C99... yes
checking for inttypes.h... (cached) yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking whether imaxabs is declared... yes
checking whether imaxdiv is declared... yes
checking whether strtoimax is declared... yes
checking whether strtoumax is declared... yes
checking whether getc_unlocked is declared... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking for mbstate_t... yes
checking for a traditional japanese locale... none
checking for a transitional chinese locale... none
checking for a french Unicode locale... none
checking for mmap... yes
checking for MAP_ANONYMOUS... yes
checking for memchr... yes
checking whether memchr works... yes
checking for C/C++ restrict keyword... __restrict
checking for ssize_t... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for working strerror function... yes
checking whether strndup is declared... yes
checking whether strnlen is declared... yes
checking for wint_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for alloca as a compiler built-in... yes
checking whether to enable assertions... yes
checking whether btowc(EOF) is correct... guessing yes
checking for GNU libc compatible calloc... yes
checking whether // is distinct from /... (cached) no
checking for error_at_line... yes
checking whether __fpending is declared... yes
checking for getpagesize... yes
checking whether the compiler generally respects inline... yes
checking whether inttypes.h conforms to C99... yes
checking whether INT32_MAX < INTMAX_MAX... yes
checking whether INT64_MAX == LONG_MAX... yes
checking whether UINT32_MAX < UINTMAX_MAX... yes
checking whether UINT64_MAX == ULONG_MAX... yes
checking for flag to ignore unused libraries... -Wl,--as-needed
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... (cached) yes
checking whether mbrtowc handles incomplete characters... guessing yes
checking whether mbrtowc works as well as mbtowc... guessing yes
checking whether mbrtowc handles a NULL string argument... guessing yes
checking whether mbrtowc has a correct return value... guessing yes
checking whether mbrtowc returns 0 when parsing a NUL character... guessing yes
checking whether mbrtowc handles incomplete characters... (cached) guessing yes
checking whether mbrtowc works as well as mbtowc... (cached) guessing yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for working re_compile_pattern... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking whether isblank is declared... yes
checking for rpmatch... yes
checking for ssize_t... (cached) yes
checking for va_copy... yes
checking whether stdint.h conforms to C99... (cached) yes
checking for random.h... no
checking for struct random_data... yes
checking for working strndup... yes
checking for working strnlen... yes
checking whether <wchar.h> is standalone... yes
checking whether mbrtowc handles incomplete characters... (cached) guessing yes
checking whether mbrtowc works as well as mbtowc... (cached) guessing yes
checking whether wcrtomb return value is correct... guessing yes
checking whether iswcntrl works... yes
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking if environ is properly declared... yes
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional japanese locale... (cached) none
checking for a transitional chinese locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for wchar_t... yes
checking for wint_t... (cached) yes
checking for unsetenv... yes
checking for unsetenv() return type... int
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional japanese locale... (cached) none
checking for a transitional chinese locale... (cached) none
checking whether wctob works... guessing yes
checking whether wctob is declared... yes
checking size of off_t... 8
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for dlopen in -ldl... yes
checking for uuid_generate in -luuid... yes
checking for dm_task_create in -ldevmapper... no
configure: error: libdevmapper could not be found, but is required for the
--enable-device-mapper option, which is enabled by default.  Either disable
device-mapper support with --disable-device-mapper or download and install
device-mapper from:
    http://sources.redhat.com/dm/
Note: if you are using precompiled packages you will need the development
package as well (it may be called device-mapper-devel or something similar).
    
There seems to be no Makefile in this directory.
You must run ./configure before running `make'.
make: *** [abort-due-to-no-makefile] Error 1
There seems to be no Makefile in this directory.
You must run ./configure before running `make'.
make: *** [abort-due-to-no-makefile] Error 1
```Entré a la página mencionada del Device-mapper Resource, pero al parecer ya tengo instaladas las librerías que no encuentra:


```
root@diego-hpcompaq:~/parted-1.9.0# apt-get install dmsetup
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
dmsetup ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
root@diego-hpcompaq:~/parted-1.9.0# apt-get install libdevmapper
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando libdevmapper1.02.1 en lugar de libdevmapper
libdevmapper1.02.1 ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
```¿Alguna sugerencia?  ¿Alguien conoce alguna manera más sencilla de instalar QtParted en Ubuntu Jacklope?
 


Si no tengo instalado el GNUParted no puedo instalar Qtparted...

---

### Post by guisheca on 2009-08-16
Te complicaste mucho la vida amigo, poné esto en un terminal y listo:

```
sudo aptitude install gparted
```

Eso te instala el gparted de forma automática, la diferencia con el qtparted es que este último tiene una interfaz gráfica pensada mas que nada para el escritorio kde, y no te digo que lo instales porque (no se porque) no se encuentra en los repositorios oficiales de ubuntu. Y además porque el gparted es lo mismo.

Saludos.

---

### Post by staar on 2009-08-16
qtparted es viejo y ya no está soportado (creo que no se desarrolla más) por eso no está más en los repos, gparted por el contrario sigue siendo mantenido y de hecho está incluido en el livecd...

saludos

---

### Post by daggaz on 2009-08-16
¡Yupi!
Gracias... Sabía que existía este programa (pues lo he usado con el Live CD), pero no sabía que podía formatear cualquier disco duro o USB con él.
Voy a probar, gracias. Ya lo instalé sin problemas : >

---

