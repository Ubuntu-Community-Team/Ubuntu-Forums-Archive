---
title: "Problema con el area de notificación de KDE 4.3 en Ubuntu 9.04"
date: 2009-10-05
forum: Software
---

### Post by emiliano_raso on 2009-10-05
Bueno, aca les adjunto un screenshot de lo que me pasa.
Acabo de instalar KDE 4.3 en Ubuntu 9.04 y en el area de notificación las aplicaciones no tienen sus iconos correspondientes, sino que "copian" el de al lado.
EXCEPTO EMESENE!
Es algo muy bizarro.

Tal vez a alguien ya le pasó, pero busqué en google y no dice nada al respecto.

---

### Post by guillermolisi on 2009-10-05
> **emiliano_raso said:**
> Bueno, aca les adjunto un screenshot de lo que me pasa.
Acabo de instalar KDE 4.3 en Ubuntu 9.04 y en el area de notificación las aplicaciones no tienen sus iconos correspondientes, sino que "copian" el de al lado.
EXCEPTO EMESENE!
Es algo muy bizarro.

Tal vez a alguien ya le pasó, pero busqué en google y no dice nada al respecto.
Vengo usando KDE 4.3 con JJ desde que se lanzo como version beta y nunca tuve esa anomalia.

---

### Post by oktubrer on 2009-10-05
No me pasó tampoco con KDE4.0/1/2/3
¿Si cambiás el tema de íconos los actualiza igual?

---

### Post by emiliano_raso on 2009-10-06
Cambié el tema de iconos y me hace lo mismo.
Lo que me llamó la atención, no creo que tenga que ver pero por las dudas lo comento porque no se casi nada de KDE, es que en:
*K menu/Preferencias del sistema/Apariencia/Iconos/Obtener temas nuevos*
Me aparece la lista de icon themes para instalar, pero cuando clickeo instalar no hace nada. Ni descarga ni nada...

En KDE lo que administra lo iconos es algo aparte?
Mas allá de eso, solamente tengo ese problema al instalar nuevos y en el area de notificación.
El resto anda perfecto.

---

### Post by manerahul on 2009-10-06
an error occured when i install .tar.gz2 file of vlc in ubuntu 9.04
while configuring... error is:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
checking for egrep... (cached) /bin/grep -E
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking dependency style of gcc -std=gnu99... gcc3
checking for ranlib... ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for dlltool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking for libs in /media/soft/soft/linux/vlc-1.0.1/./extras/contrib... no
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... ld
checking if the linker (ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... (cached) pass_all
checking for ar... (cached) ar
checking for strip... (cached) strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... ld
checking if the linker (ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for buggy GNU/libc versions... not present
checking for shared objects suffix... .so
checking for gettimeofday... yes
checking for isatty... yes
checking for sigrelse... yes
checking for getpwuid_r... yes
checking for memalign... yes
checking for posix_memalign... yes
checking for if_nametoindex... yes
checking for getenv... yes
checking for putenv... yes
checking for setenv... yes
checking for ctime_r... yes
checking for lrintf... no
checking for daemon... yes
checking for fork... yes
checking for lstat... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for uselocale... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for fcntl... yes
checking for asprintf... yes
checking for atof... yes
checking for atoll... yes
checking for getcwd... yes
checking for gmtime_r... yes
checking for lldiv... yes
checking for localtime_r... yes
checking for rewind... yes
checking for strcasecmp... yes
checking for strcasestr... yes
checking for strdup... yes
checking for strlcpy... no
checking for strncasecmp... yes
checking for strndup... yes
checking for strnlen... yes
checking for strsep... yes
checking for strtof... yes
checking for strtoll... yes
checking for vasprintf... yes
checking for swab... yes
checking for stricmp... no
checking for strnicmp... no
checking for fdatasync... yes
checking for vmsplice... yes
checking for mmap... yes
checking for setlocale... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for nl_langinfo... yes
checking for nl_langinfo and CODESET... yes
checking for connect... yes
checking for send... yes
checking for socklen_t in sys/socket.h... yes
checking for struct sockaddr_storage... yes
checking for library containing getaddrinfo... none required
checking for getnameinfo... yes
checking for gai_strerror... yes
checking for struct addrinfo... yes
checking for va_copy... yes
checking for __va_copy... yes
checking for inet_aton... yes
checking for getopt_long... yes
checking return type of signal handlers... void
checking for cos in -lm... yes
checking for pow in -lm... yes
checking for sqrt in -lm... yes
checking for ceil in -lm... yes
checking for exp in -lm... yes
checking for round in -lm... yes
checking for sqrtf in -lmx... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for shl_load... (cached) no
checking for dld_link in -ldld... no
checking image.h usability... no
checking image.h presence... no
checking for image.h... no
checking for load_add_on... no
checking for dlfcn.h... (cached) yes
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for main in -lpthread... yes
checking for clock_nanosleep in -lrt... yes
checking for nanosleep... yes
checking for strncasecmp in strings.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for strings.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for sys/types.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/udplite.h usability... no
checking netinet/udplite.h presence... no
checking for netinet/udplite.h... no
checking sys/eventfd.h usability... yes
checking sys/eventfd.h presence... yes
checking for sys/eventfd.h... yes
checking for net/if.h... yes
checking machine/param.h usability... no
checking machine/param.h presence... no
checking for machine/param.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for ssize_t... yes
checking for library containing poll... none required
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for nanosleep in time.h... yes
checking for timespec in sys/time.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for HAL... no
configure: WARNING: libhal >= 0.5.0 was not found. Install libhal-dev ?
checking for MTP... no
configure: WARNING: MTP library not found
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?


how do get libhal-dev & libdbus-dev for my OS ubuntu 9.04  pls help me....

---

### Post by emiliano_raso on 2009-10-06
Me metí en: [https://bugs.kde.org/](https://bugs.kde.org/) a ver si encontraba algo.
En la busqueda puse **system tray** y me tira todos los siguientes resultados, y realmente no se cual sería mi problema:
[https://bugs.kde.org/buglist.cgi?quicksearch=system+tray](https://bugs.kde.org/buglist.cgi?quicksearch=system+tray)

---

### Post by emiliano_raso on 2009-10-09
Actualicé a KDE 4.3.2 y sigo en la misma :-S
Probé:
- Cambiar los temas de plasma
- Cambiar los temas de iconos
- Cambiar el estilo
- Cambiar de lugar los paneles
- Cambiar de lugar el System Tray
- Cambiar los efectos de escritorio (activando y desactivando)

Y no sirvió de nada. La unica diferencia es que cuando pongo el panel a la izquierda/derecha de la pantalla de forma vertical, los iconos en vez de duplicarse como en el screenshot, simplemente no aparecen pero hay un espacio sin embargo, ya que realmente está.

---

### Post by staar on 2009-10-09
probaste con una configuración limpia de KDE, borrando/cambiando de nombre la carpeta .kde4 de tu home?

saludos

---

### Post by emiliano_raso on 2009-10-09
> **staar said:**
> probaste con una configuración limpia de KDE, borrando/cambiando de nombre la carpeta .kde4 de tu home?

saludos

No entendí :-S Explicate mejor.

---

### Post by staar on 2009-10-09
al cambiar de nombre (o borrar) la carpeta oculta *.kde4* que está dentro de tu home, la siguiente vez que inicies sesión la configuración de kde4 va a volver a su valores por defecto, con esto descartas que sea un tema de archivos de configuración corruptos (algo que no es raro entre versiones de kde4), al mismo resultado podés llegar si creas un nuevo usuario e inicias con él, si el problema no pasa es un tema de configuraciones...

saludos

---

### Post by emiliano_raso on 2009-10-09
Acabo de probar, y sigue pasando lo mismo :-S

---

### Post by emiliano_raso on 2010-06-15
Resuelto en las nuevas versiones de KDE.

---

