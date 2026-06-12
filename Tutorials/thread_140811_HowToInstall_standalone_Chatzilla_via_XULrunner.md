---
title: "HowTo:Install standalone Chatzilla via XULrunner"
date: 2006-03-07
forum: Tutorials
---

### Post by gord on 2006-03-07
hi :)

This is a little howto on installing the mozilla Chatzilla IRC client via XULrunner, thus allowing it to run 'standalone'. perfect for those of you that what a prittyer irc client or are just bored with what you have now. 

first you should note that XULRunner is still in its development phase so it might not work perfectly (allthough i have encountered no problems). 

first of all, we need to get ourselfs a copy of XULRunner, which is the base on which Chatzilla runs. its a good 8mb or so, so give it a few mins.

```

wget http://ftp.mozilla.org/pub/mozilla.org/xulrunner/nightly/latest-mozilla1.8.0/xulrunner-1.8.0.2.en-US.linux-i686.tar.gz
sudo tar -C /opt -xzvf xulrunner-1.8.0.2.en-US.linux-i686.tar.gz
rm xulrunner-1.8.0.2.en-US.linux-i686.tar.gz
sudo ln -s /opt/xulrunner/xulrunner /usr/bin/xulrunner

```


next we need to get a version of chatzilla designed to run with XULRunner. this code gets files that might not be around forever, so if you encounter errors you can get the latest from [here](http://chatzilla.rdmsoft.com/xulrunner/)
```

wget http://chatzilla.rdmsoft.com/xulrunner/download/chatzilla-0.9.72-xr.zip
sudo mkdir /opt/xulrunner/chatzilla
sudo unzip -d "/opt/xulrunner/chatzilla" chatzilla-0.9.72-xr.zip
rm chatzilla-0.9.72-xr.zip

```

and thats about it :) to run chatzilla you will need to do
```

xulrunner --app "/opt/xulrunner/chatzilla/application.ini"

```
so i suggest creating a launcher in the gnome menu's or desktop.

you can find more 'motif's to change the look of chatzilla [here](http://www.hacksrus.com/~ginda/chatzilla/motifs.html), or just create your own :)

screenys:
[[IMG]http://img357.imageshack.us/img357/3914/screenshotdark3id.th.png[/IMG]](http://img357.imageshack.us/my.php?image=screenshotdark3id.png) [[IMG]http://img357.imageshack.us/img357/4787/screenshotlight1hi.th.png[/IMG]](http://img357.imageshack.us/my.php?image=screenshotlight1hi.png)

---

### Post by rCXer on 2009-05-20
Thank you for posting this :-D.  It worked perfectly after I updated the paths. Here is the updated version...
```
wget [COLOR="Red"]http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.9.0.7/runtimes/xulrunner-1.9.0.7.en-US.linux-i686.tar.bz2[/COLOR]
sudo tar -C /opt [COLOR="Red"]-xvjf xulrunner-1.9.0.7.en-US.linux-i686.tar.bz2[/COLOR]
rm [COLOR="Red"]xulrunner-1.9.0.7.en-US.linux-i686.tar.bz2[/COLOR]
sudo ln -s /opt/xulrunner/xulrunner /usr/bin/xulrunner
```

```
wget http://chatzilla.rdmsoft.com/xulrunner/download/[COLOR="Red"]chatzilla-0.9.84-xr.zip[/COLOR]
sudo mkdir /opt/xulrunner/chatzilla
sudo unzip -d "/opt/xulrunner/chatzilla" [COLOR="Red"]chatzilla-0.9.84-xr.zip[/COLOR]
rm [COLOR="Red"]chatzilla-0.9.84-xr.zip[/COLOR]
```

I then made a launcher with the command...
```
xulrunner -app "/opt/xulrunner/chatzilla/application.ini"
```

---

### Post by Chriswaterguy on 2009-12-15
I'm using Ubuntu 8.10* and XULrunner is installed (says synaptic) but not in opt. Should I unpack ChatZilla into one of these directories?
[LIST]
[*]/usr/lib/xulrunner
[*]/usr/lib/xulrunner-1.9.0.14
[*]/usr/lib/xulrunner-addons
[/LIST]

Thanks!

*Crunchbang actually, which is basically Ubuntu with a different window manager.

---

### Post by rCXer on 2009-12-16
In your case, you can just unpack the contents of the archive to a new "chatzilla" folder in the 2nd location...
```

/usr/lib/xulrunner-1.9.0.14/chatzilla/

```

Then create a launcher on the desktop with...
```

/usr/lib/xulrunner-1.9.0.14/xulrunner -app "/usr/lib/xulrunner-1.9.0.14/chatzilla/application.ini"

```
...as the command.  You can also use an official chatzilla icon for the launcher.  In your case, the icons would be in...
```

/usr/lib/xulrunner-1.9.0.14/chatzilla/chrome/icons/default/chatzilla-window.ico

```

---

### Post by Vampe on 2010-09-09
Like rCXer it worked perfectly after updating paths, posting new updated version!!!
```
wget http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases[COLOR="Red"]/1.9.2.8/runtimes/xulrunner-1.9.2.8.en-US.linux-i686.tar.bz2[/COLOR]
sudo tar -C /opt -xvjf [COLOR="Red"]xulrunner-1.9.2.8.en-US.linux-i686.tar.bz2[/COLOR]
rm [COLOR="Red"]xulrunner-1.9.2.8.en-US.linux-i686.tar.bz2[/COLOR]
sudo ln -s /opt/xulrunner/xulrunner /usr/bin/xulrunner
```

```
wget http://chatzilla.rdmsoft.com/xulrunner/download/[COLOR="Red"]chatzilla-0.9.86-xr.zip[/COLOR]
sudo mkdir /opt/xulrunner/chatzilla
sudo unzip -d "/opt/xulrunner/chatzilla" [COLOR="Red"]chatzilla-0.9.86-xr.zip[/COLOR]
rm [COLOR="Red"]chatzilla-0.9.86-xr.zip[/COLOR]
```

I then used same command as rCXer for my launcher
```
xulrunner -app "/opt/xulrunner/chatzilla/application.ini"
```

---

### Post by JamesTheAwesomeDude on 2013-01-08
Okay, the URL for the first command was faulty. I did some poking around, and fixed it (it's ftp.mozilla.org, not releases.mozilla.org,) only difference is, I'm running 1.9.2.19 instead of 1.9.2.8.
Next, I got it installed to /opt/xulrunner, and linked the executable to /usr/bin.

After that, I downloaded and extracted Chatzilla XUL (version 0.9.89.)

Finally, I launched it:
```
james@james-OptiPlex-GX620:~$ /opt/xulrunner/xulrunner -app "/opt/xulrunner/chatzilla/application.ini"
/opt/xulrunner/xulrunner-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
james@james-OptiPlex-GX620:~$ 
```

Running Nautilus as Root, I searched /opt/xulrunner for any file with "libgtk" in the name, but there were no results.

I decided to attempt to compile it myself, and here's the result...```
james@james-OptiPlex-GX620:~/gtk+-2.0.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for some Win32 platform... no
checking for native Win32... no
checking whether build environment is sane... yes
checking for strerror in -lcposix... no
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.0.6 atk >= 1.0.1 pango >= 1.0.1... yes
checking BASE_DEPENDENCIES_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0  
checking BASE_DEPENDENCIES_LIBS... -latk-1.0 -lpango-1.0 -lgobject-2.0 -lglib-2.0  
checking Whether to write dependencies into .pc files... no
checking for perl5... no
checking for perl... /usr/bin/perl
checking for indent... no
checking for lstat... yes
checking for mkstemp... yes
checking for flockfile... yes
checking for sigsetjmp... yes
checking whether make is GNU Make... yes
checking for ranlib... (cached) ranlib
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  am ar az be bg ca cs cy da de el en_GB en@IPA es et eu fa fi fr ga gl he hi hr hu ia it ja ko lt lv ms nl nn no pl pt pt_BR ro ru sk sl sp sr sv tr uk vi wa zh_TW zh_CN
checking for extra flags to get ANSI library prototypes... none needed
checking for the BeOS... no
checking for extra flags for POSIX compliance... none needed
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.6... yes (version 2.32.3)
checking for bind_textdomain_codeset... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking whether byte ordering is bigendian... no
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... (cached) yes
checking return type of signal handlers... void
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking for getresuid... yes
checking for uid_t in sys/types.h... yes
checking for fd_set... yes, found in sys/types.h
checking for wchar.h... yes
checking for wctype.h... yes
checking for iswalnum... yes
checking if iswalnum() and friends are properly defined... yes
checking whether to build gmodulized gdk-pixbuf... yes
checking whether dynamic modules work... yes
checking for TIFFReadScanline in -ltiff... yes
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for jpeg_destroy_decompress in -ljpeg... yes
checking for jpeglib.h... yes
checking for jpeg_simple_progression in -ljpeg... yes
checking for libpng12... yes
checking pixbuf loaders to build... 
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... (cached) void
checking for x86 platform... no
checking for freetype-config... /usr/bin/freetype-config
checking for FT_New_Face in -lfreetype... yes
checking For sufficiently new FreeType (at least 2.0.1)... no
configure: error: pangoxft Pango backend found but did not find freetype libraries
james@james-OptiPlex-GX620:~/gtk+-2.0.9$ 
```

I downloaded, built, and installed FreeType, then tried again, but with the same result.
At this point, I gave up trying to build it myself. I never have much luck building other peoples' code and it only leads to frustration. (Managing to successfully build FreeType was a fluke.)

After MUCH searching, I finally found the package "gtk+2.0". After installing it (which took FOREVER,) I STILL got the same error.

So, I ran a search for "libgtk" across the whole filesystem, and finally found the exact file I needed: "libgtk-11x-2.0.so.0" in /usr/lib/x86_64-linux-gnu (the file was a symbolic link to a file "libgtk-x11-2.0.so.0.2400.10" in the same directory.)

```
james@james-OptiPlex-GX620:~$ ln -s /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.10 /opt/xulrunner
james@james-OptiPlex-GX620:~$ mv libgtk-x11-2.0.so.0.2400.10 libgtk-x11-2.0.so
james@james-OptiPlex-GX620:~$ xulrunner -app "/opt/xulrunner/chatzilla/application.ini"
/opt/xulrunner/xulrunner-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: wrong ELF class: ELFCLASS64
james@james-OptiPlex-GX620:~$ 
```
At this point, I am completely out of ideas. My knowledgebase has been emptied.
I now turn to the Ubuntu community.

---

