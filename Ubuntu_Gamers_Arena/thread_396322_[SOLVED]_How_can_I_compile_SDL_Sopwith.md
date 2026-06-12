---
title: "[SOLVED] How can I compile SDL Sopwith"
date: 2007-03-29
forum: Ubuntu Gamers Arena
---

### Post by holihue on 2007-03-29
How can I compile SDL Sopwith from source?

I always get this message:

supr@hk-laptop:~$ cd Desktop/sdl_sopwith-1.7.1/
supr@hk-laptop:~/Desktop/sdl_sopwith-supr@hk-laptop:~$ cd Desktop/sdl_sopwith-1.7.1/
supr@hk-laptop:~/Desktop/sdl_sopwith-1.7.1$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for a BSD compatible install... /usr/bin/install -c
checking for sdl-config... (cached) /usr/bin/sdl-config
checking for SDL - version >= 1.1.3... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for glib-2.0 >= 2.0 gtk+-2.0 >= 2.0... yes
checking GTK_CFLAGS... -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking GTK_LIBS... -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking how to run the C preprocessor... (cached) gcc -E
checking for netinet/ip.h... (cached) yes
creating ./config.status
creating Makefile
creating src/Makefile
creating src/gtk/Makefile
creating src/sdl/Makefile
creating src/psion/Makefile
creating doc/Makefile
creating config.h
config.h is unchanged
supr@hk-laptop:~/Desktop/sdl_sopwith-1.7.1$ make
make  all-recursive
make[1]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1'
Making all in src
make[2]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
Making all in sdl
make[3]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/sdl'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/sdl'
Making all in gtk
make[3]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/gtk'
make[3]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I.. -c swsound.c
swsound.c:82: error: static declaration of ‘titleflg’ follows non-static declaration
swmain.h:49: error: previous declaration of ‘titleflg’ was here
make[3]: *** [swsound.o] Error 1
make[3]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1'
make: *** [all-recursive-am] Error 2
supr@hk-laptop:~/Desktop/sdl_sopwith-1.7.1$ 
1.7.1$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for a BSD compatible install... /usr/bin/install -c
checking for sdl-config... (cached) /usr/bin/sdl-config
checking for SDL - version >= 1.1.3... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for glib-2.0 >= 2.0 gtk+-2.0 >= 2.0... yes
checking GTK_CFLAGS... -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking GTK_LIBS... -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking how to run the C preprocessor... (cached) gcc -E
checking for netinet/ip.h... (cached) yes
creating ./config.status
creating Makefile
creating src/Makefile
creating src/gtk/Makefile
creating src/sdl/Makefile
creating src/psion/Makefile
creating doc/Makefile
creating config.h
config.h is unchanged
supr@hk-laptop:~/Desktop/sdl_sopwith-1.7.1$ make
make  all-recursive
make[1]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1'
Making all in src
make[2]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
Making all in sdl
make[3]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/sdl'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/sdl'
Making all in gtk
make[3]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src/gtk'
make[3]: Entering directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I.. -c swsound.c
swsound.c:82: error: static declaration of ‘titleflg’ follows non-static declaration
swmain.h:49: error: previous declaration of ‘titleflg’ was here
make[3]: *** [swsound.o] Error 1
make[3]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/supr/Desktop/sdl_sopwith-1.7.1'
make: *** [all-recursive-am] Error 2
supr@hk-laptop:~/Desktop/sdl_sopwith-1.7.1$ 

Thanks

---

### Post by Programmerer on 2007-10-21
When I have problems with compiling do I use to search in the code after some packages that I may have to install.

And if the program you try to compile is in Synaptic can you try this command:

```
sudo apt-get build-dep "package"
```

Good luck, but I think you can find better games for Ubuntu now-a-days:)
[COLOR="Silver"]
[SIZE="1"]Or are you just trying to modify the source?[/SIZE][/COLOR]

---

### Post by holihue on 2007-10-21
> **Programmerer said:**
> When I have problems with compiling do I use to search in the code after some packages that I may have to install.

And if the program you try to compile is in Synaptic can you try this command:

```
sudo apt-get build-dep "package"
```

Good luck, but I think you can find better games for Ubuntu now-a-days:)
[COLOR="Silver"]
[SIZE="1"]Or are you just trying to modify the source?[/SIZE][/COLOR]


I did that.
It did not work.

The problem was in the source.

The source I used was downloaded from internet.
I had to use another source:
```
sudo apt-get source sopwith
```

---

