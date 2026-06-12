---
title: "kubuntu"
date: 2009-02-03
forum: Software
---

### Post by tsueseres on 2009-02-03
hola, en el panel me aparecen todas las ventanas por ejemplo tengo 4 escritorios, tengo 2 ventanas abiertas en el cuarto escritorio  y otras 2 en el primero, pero el panel me las muestra todas 

donde se puede cambiar esta configuracion

---

### Post by Hei Ku on 2009-02-03
En qué version? La KDE 3.5, haciendo click derecho sobre el panel podes entrar a la configuracion, de ahi a barra de tareas y ahi seleccionar que solo te muestre las tareas del escritorio activo. Creo que KDE4.1 tenia pocas opciones, y el 4.2 tiene varias opciones mas que estas, como agrupamiento y esas cosas.

---

### Post by tsueseres on 2009-02-03
> **Hei Ku said:**
> En qué version? La KDE 3.5, haciendo click derecho sobre el panel podes entrar a la configuracion, de ahi a barra de tareas y ahi seleccionar que solo te muestre las tareas del escritorio activo. Creo que KDE4.1 tenia pocas opciones, y el 4.2 tiene varias opciones mas que estas, como agrupamiento y esas cosas.

hola tengo la version 3.5.10 pero no me aparece lo que me estas diciendo
porcierto tengo el compiz instalado con la opcion del cubo lo cual tuve que quitar los demas escritorios 

la unica forma de que me apareca esa opcion es desactivando los escritorios creados por el cubo pero queiro tener el cubo y esa opcion, no hay manera de hacerlo?

---

### Post by Hei Ku on 2009-02-03
En kde-apps.org hay un administrador de tareas patcheado para Compiz, y recuerdo que habia algun comentario en particular para activar esa opcion.
Vas a tener que bajarlo y compilarlo porque no estaba para Kubuntu.
El problema con Compiz viene porque Compiz y KDE manejan los escritorios de manera fundamentalmente diferente. Para Compiz (y Gnome) es todo un gran escritorio y tenes viewports. Para KDE realmente son escritorios diferentes.

---

### Post by tsueseres on 2009-02-03
> **Hei Ku said:**
> En kde-apps.org hay un administrador de tareas patcheado para Compiz, y recuerdo que habia algun comentario en particular para activar esa opcion.
Vas a tener que bajarlo y compilarlo porque no estaba para Kubuntu.
El problema con Compiz viene porque Compiz y KDE manejan los escritorios de manera fundamentalmente diferente. Para Compiz (y Gnome) es todo un gran escritorio y tenes viewports. Para KDE realmente son escritorios diferentes.
thanks

---

### Post by tsueseres on 2009-02-03
> **Hei Ku said:**
> En kde-apps.org hay un administrador de tareas patcheado para Compiz, y recuerdo que habia algun comentario en particular para activar esa opcion.
Vas a tener que bajarlo y compilarlo porque no estaba para Kubuntu.
El problema con Compiz viene porque Compiz y KDE manejan los escritorios de manera fundamentalmente diferente. Para Compiz (y Gnome) es todo un gran escritorio y tenes viewports. Para KDE realmente son escritorios diferentes.

hola, oye nomas que encontre una version para el kde pero con opensuse yo tengo ubuntu 8.04, no sabes como hacerle en este caso

gracias

---

### Post by Hei Ku on 2009-02-04
[http://www.kde-apps.org/content/show.php/taskbar-compiz+for+kde-3.5.10?content=89500](http://www.kde-apps.org/content/show.php/taskbar-compiz+for+kde-3.5.10?content=89500)

Baja esta y compilala. Despues de instalarla la agregas con el boton derecho.

---

### Post by tsueseres on 2009-02-04
> **Hei Ku said:**
> [http://www.kde-apps.org/content/show.php/taskbar-compiz+for+kde-3.5.10?content=89500](http://www.kde-apps.org/content/show.php/taskbar-compiz+for+kde-3.5.10?content=89500)

Baja esta y compilala. Despues de instalarla la agregas con el boton derecho.

ola ya trate de compilarla pero no **** 

le pongo cd del directorio luego

./configure  
aparecen muchas cosas
luego le pongo 

make 
y dice que no se puede, deecho siempre que trato de compilar un programa en esta parte de make nunca puedo, no se si este haciendo algo mal

---

### Post by Hei Ku on 2009-02-04
que error te aparece? Sin el error en concreto no podemos hacer nada.


"In God we trust, all others bring data"

---

### Post by tsueseres on 2009-02-04
> **Hei Ku said:**
> que error te aparece? Sin el error en concreto no podemos hacer nada.


"In God we trust, all others bring data"

esto es todo lo que me sale

```
 luis@UMI:~$ cd /home/luis/Escritorio/89500-taskbar-compiz/taskbar-compiz
luis@UMI:~/Escritorio/89500-taskbar-compiz/taskbar-compiz$ ./configurechecking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
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
checking how to run the C preprocessor... gcc -E
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
luis@UMI:~/Escritorio/89500-taskbar-compiz/taskbar-compiz$ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
luis@UMI:~/Escritorio/89500-taskbar-compiz/taskbar-compiz$ 

```

---

### Post by Hei Ku on 2009-02-05
El problema es que no tenes instalado los paquetes para poder compilar.

sudo aptitude install build-essential


Despues de eso, volve a probar y postea el error que te tire.

---

### Post by tsueseres on 2009-02-07
> **Hei Ku said:**
> El problema es que no tenes instalado los paquetes para poder compilar.

sudo aptitude install build-essential


Despues de eso, volve a probar y postea el error que te tire.

```
  
luis@UMI:~$ cd /home/luis/Escritorio/89500-taskbar-compiz/taskbar-compiz
luis@UMI:~/Escritorio/89500-taskbar-compiz/taskbar-compiz$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
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
checking for msgfmt... msgfmt
checking for gmsgfmt... msgfmt
found msgfmt program is not GNU msgfmt; ignore it
checking for xgettext... :
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking for PIE support... yes
checking if enabling -pie/fPIE support... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
luis@UMI:~/Escritorio/89500-taskbar-compiz/taskbar-compiz$ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
luis@UMI:~/Escritorio/89500-taskbar-compiz/taskbar-compiz$ 

```

---

### Post by Hei Ku on 2009-02-07
Poné:

```

sudo aptitude install kdelibs4-dev

```

Y andá a tomarte un café, porque va a bajar como 100MB. :p

---

### Post by tsueseres on 2009-02-09
> **Hei Ku said:**
> Poné:

```

sudo aptitude install kdelibs4-dev

```

Y andá a tomarte un café, porque va a bajar como 100MB. :p

gracias

---

