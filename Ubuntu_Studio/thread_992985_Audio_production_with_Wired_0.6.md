---
title: "Audio production with Wired 0.6"
date: 2008-11-25
forum: Ubuntu Studio
---

### Post by Uwouldntlisten on 2008-11-25
I have installed Wired 0.6 on Intrepid, with much frustration and help from more skilled friends. But now, I see I do not have any sound packs. I have instruments but no patches for them. Did I miss something in installation? Does anyone know where I can get audio files? It seems to prefer .wav.

---

### Post by ceeleelewis on 2008-12-26
Hi, 

Just wondering if you can share your steps of finally get wired installed. I've been beating my head with this install all day. 

Here's the error I'm constantly getting (before you ask... yes I've read the INSTALL section of wired)

sudo ./autogen
sudo ./configure --disable-portaudio
[sudo] password for clewis: 
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
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether gcc needs -traditional... no
checking how to run the C++ preprocessor... g++ -E
checking for pthread_create in -lpthread... yes
checking for sf_open in -lsndfile... yes
checking for xmlParseMemory in -lxml2... yes
checking for src_new in -lsamplerate... yes
checking for soundtouch_ac_test in -lSoundTouch... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.6.0... yes (version 2.6.3)
checking for wxWidgets static library... no
checking for wx-config... /usr/bin/wx-config
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SAMPLERATE... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for dlfcn.h... (cached) yes
checking for stdint.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking cmath usability... yes
checking cmath presence... yes
checking for cmath... yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking list.h usability... no
checking list.h presence... no
checking for list.h... no
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking direct.h usability... no
checking direct.h presence... no
checking for direct.h... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking sndfile.h usability... yes
checking sndfile.h presence... yes
checking for sndfile.h... yes
checking samplerate.h usability... yes
checking samplerate.h presence... yes
checking for samplerate.h... yes
checking soundtouch/SoundTouch.h usability... yes
checking soundtouch/SoundTouch.h presence... yes
checking for soundtouch/SoundTouch.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for working volatile... yes
checking whether closedir returns void... no
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether lstat accepts an empty string... no
checking whether lstat dereferences a symlink specified with a trailing slash... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for floor... yes
checking for ftime... yes
checking for getcwd... yes
checking for memmove... yes
checking for memset... yes
checking for pow... yes
checking for select... yes
checking for sqrt... yes
checking for strdup... yes
checking for memset... (cached) yes
checking for open... yes
checking for enable-optimize... 
checking for enable-debug... No
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... (cached) ranlib
checking for strerror in -lcposix... no
checking for signed... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... 18446744073709551615UL
checking for stdint.h... (cached) yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
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
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... (cached) yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... (cached) yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... yes
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating intl/Makefile
config.status: WARNING:  intl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: creating src/save/Makefile
config.status: creating src/audio/Makefile
config.status: creating src/editmidi/Makefile
config.status: creating src/engine/Makefile
config.status: creating src/fileloader/Makefile
config.status: creating src/gui/Makefile
config.status: creating src/midi/Makefile
config.status: creating src/mixer/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/redist/Makefile
config.status: creating src/sequencer/Makefile
config.status: creating src/dssi/Makefile
config.status: creating src/undo/Makefile
config.status: creating src/libs/Makefile
config.status: creating src/libs/WiredWidgets/Makefile
config.status: creating src/libs/WiredWidgets/src/Makefile
config.status: creating src/libs/WiredAkai/Makefile
config.status: creating src/libs/WiredAkai/src/Makefile
config.status: creating src/data/Makefile
config.status: creating src/data/ihm/Makefile
config.status: creating src/data/ihm/mixer/Makefile
config.status: creating src/data/ihm/opt/Makefile
config.status: creating src/data/ihm/player/Makefile
config.status: creating src/data/ihm/seqtrack/Makefile
config.status: creating src/data/ihm/splash/Makefile
config.status: creating src/data/ihm/toolbar/Makefile
config.status: creating src/data/ihm/widgets/Makefile
config.status: creating src/data/plugins/Makefile
config.status: creating src/data/dssi/Makefile
config.status: creating src/conf/Makefile
config.status: creating src/xml/Makefile
config.status: creating src/samplerate/Makefile
config.status: creating src/codec/Makefile
config.status: creating src/wiredvideo/Makefile
config.status: creating src/plugins/beatbox/Makefile
config.status: creating src/plugins/compressor/Makefile
config.status: creating src/plugins/crusher/Makefile
config.status: creating src/plugins/delay/Makefile
config.status: creating src/plugins/filter/Makefile
config.status: creating src/plugins/loop_sampler/Makefile
config.status: creating src/plugins/akai_sampler/Makefile
config.status: creating src/plugins/reverb/Makefile
config.status: creating src/plugins/synth/Makefile
config.status: creating src/plugins/chorus/Makefile
config.status: creating src/plugins/wahwah/Makefile
config.status: creating src/plugins/test/Makefile
config.status: creating src/data/plugins/akaisampler/Makefile
config.status: creating src/data/plugins/beatbox/Makefile
config.status: creating src/data/plugins/compressor/Makefile
config.status: creating src/data/plugins/crusher/Makefile
config.status: creating src/data/plugins/delay/Makefile
config.status: creating src/data/plugins/filter/Makefile
config.status: creating src/data/plugins/loopsampler/Makefile
config.status: creating src/data/plugins/reverb/Makefile
config.status: creating src/data/plugins/wahwah/Makefile
config.status: creating src/data/plugins/chorus/Makefile
config.status: creating src/midi/portmidi/Makefile
config.status: creating src/midi/portmidi/porttime/Makefile
config.status: creating src/include/config.h
config.status: src/include/config.h is unchanged
config.status: executing libtool commands
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile

-=-=-=-=-=-=-=-=-=-= Configuration Complete =-=-=-=-=-=-=-=-=-=-=-

  Configuration summary :

    Version : ..................... 0.6
    Enable debugging : ............ No
    Enable optimizations : ........ Yes


   Tools :

     Compiler is GCC : ............. yes
     GCC major version : ........... 4


  Extra tools required :

    wxWidgets : ................... 2.6.3
    libsamplerate : ............... 0.1.3
    libsndfile : .................. 1.0.17
 
  Installation directories :
    Wired plugins directory: .............. /usr/local/lib/wired
    Wired binary directory : .............. /usr/local/bin
    Wired data directory   : .............. /usr/local/share
    Wired conf directory   : .............. /usr/local/etc/wired


sudo make
Making all in intl
make[1]: Entering directory `/home/clewis/musicapps/wired-0.6/intl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/clewis/musicapps/wired-0.6/intl'
Making all in po
make[1]: Entering directory `/home/clewis/musicapps/wired-0.6/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/clewis/musicapps/wired-0.6/po'
Making all in src
make[1]: Entering directory `/home/clewis/musicapps/wired-0.6/src'
Making all in save
make[2]: Entering directory `/home/clewis/musicapps/wired-0.6/src/save'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/clewis/musicapps/wired-0.6/src/save'
Making all in gui
make[2]: Entering directory `/home/clewis/musicapps/wired-0.6/src/gui'
g++ -DHAVE_CONFIG_H -I. -I../../src/include   -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA  -I../samplerate -I../xml -I../save -I../audio -I../libs/WiredAkai/include -I../plugins -I../fileloader -I/opt/gnome/include -I../sequencer -I../redist -I../engine -I../mixer -I../midi -I../midi/portmidi/pm_common -I../midi/portmidi/porttime -I../asm -I../editmidi -I../undo -I../libs/WiredWidgets/src -I../wiredvideo -I../codec -I../dssi `xml2-config --cflags ` -I../   -Os -MT AudioPattern.o -MD -MP -MF .deps/AudioPattern.Tpo -c -o AudioPattern.o AudioPattern.cpp
In file included from AudioPattern.cpp:17:
../engine/AudioEngine.h:121: error: expected ‘;’ before ‘(’ token
../engine/AudioEngine.h:134: error: expected ‘,’ or ‘...’ before ‘*’ token
../engine/AudioEngine.h:136: error: ISO C++ forbids declaration of ‘PaStreamCallbackTimeInfo’ with no type
../engine/AudioEngine.h: In function ‘int AudioCallback(const void*, void*, long unsigned int, int)’:
../engine/AudioEngine.h:138: error: ‘userData’ was not declared in this scope
../engine/AudioEngine.h:141: error: ‘userData’ was not declared in this scope
make[2]: *** [AudioPattern.o] Error 1
make[2]: Leaving directory `/home/clewis/musicapps/wired-0.6/src/gui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/clewis/musicapps/wired-0.6/src'
make: *** [all-recursive] Error 1

****I've literally worked on this all day. I've tried a number of things to get this to work.

---

### Post by vector.kerr on 2009-01-29
I'd just like to echo ceeleelewis. I get as far as make, and it then bombs out at the same location.

From AudioEngine.h:
```

116.  private:
117.   void                  GetAudioSystems();
118.   void                  GetDevices();
119.   void                  SetInputDevice(void);
120.   void                  SetOutputDevice(void);
121.   Device*               GetDeviceById(PaDeviceIndex id);
122.   AudioSystem*          GetAudioSystemById(int id);
123. 
124.   void                  AlertDialog(const wxString& from, const wxString& msg);
125.   PaStream              *Stream;
126. };
127.
128. extern AudioEngine      *Audio;
129. 
130. // AudioCallback
131. static int      AudioCallback(const void *input,
132.                               void *output,
133.                               unsigned long frameCount,
134.                               const PaStreamCallbackTimeInfo* timeInfo,
135.                               PaStreamCallbackFlags statusFlags,
136.                               void *userData)
137. {
138.   if (!userData)
139.     return (0);
140. 
141.   callback_t *data = (callback_t*)userData;
142.   unsigned long bytes = frameCount, processed = 0;

```

The errors for me kick in at line 121 (identical to ceeleelewis) as below:

```

In file included from AudioPattern.cpp:17:
../engine/AudioEngine.h:121: error: expected ‘;’ before ‘(’ token
../engine/AudioEngine.h:134: error: expected ‘,’ or ‘...’ before ‘*’ token
../engine/AudioEngine.h:136: error: ISO C++ forbids declaration of ‘PaStreamCallbackTimeInfo’ with no type
../engine/AudioEngine.h: In function ‘int AudioCallback(const void*, void*, long unsigned int, int)’:
../engine/AudioEngine.h:138: error: ‘userData’ was not declared in this scope
../engine/AudioEngine.h:141: error: ‘userData’ was not declared in this scope
make[2]: *** [AudioPattern.o] Error 1
make[2]: Leaving directory `/home/vector/Downloads/Applications/wired-0.6/src/gui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vector/Downloads/Applications/wired-0.6/src'
make: *** [all-recursive] Error 1

```

But nothing seems out of the ordinary to me. The only things that stand out to me are **Device*** and **PaDeviceIndex id**. I'm not going to pretend to be an expert but as a stab in the dark, could there be a problem with either of those definitions? Something to think about.

I'm running Intrepid (8.10) under the AMD64 architecture. Any assistance would be greatly appreciated. :)

---

### Post by neu2buntu on 2009-01-30
```
ioPattern.o AudioPattern.cpp
In file included from AudioPattern.cpp:17:
../engine/AudioEngine.h:9:23: error: portaudio.h: No such file or directory
In file included from AudioPattern.cpp:17:
../engine/AudioEngine.h:121: error: expected ‘;’ before ‘(’ token
../engine/AudioEngine.h:125: error: ISO C++ forbids declaration of ‘PaStream’ with no type
../engine/AudioEngine.h:125: error: expected ‘;’ before ‘*’ token
../engine/AudioEngine.h:134: error: expected ‘,’ or ‘...’ before ‘*’ token
../engine/AudioEngine.h:136: error: ISO C++ forbids declaration of ‘PaStreamCallbackTimeInfo’ with no type
../engine/AudioEngine.h: In function ‘int AudioCallback(const void*, void*, long unsigned int, int)’:
../engine/AudioEngine.h:138: error: ‘userData’ was not declared in this scope
../engine/AudioEngine.h:141: error: ‘userData’ was not declared in this scope
../engine/AudioEngine.h:150: error: ‘paFloat32’ was not declared in this scope
../engine/AudioEngine.h:178: error: ‘paInt32’ was not declared in this scope
../engine/AudioEngine.h:182: error: ‘paInt24’ was not declared in this scope
../engine/AudioEngine.h:184: error: ‘paInt16’ was not declared in this scope
../engine/AudioEngine.h:186: error: ‘paUInt8’ was not declared in this scope
../engine/AudioEngine.h:188: error: ‘paInt8’ was not declared in this scope
make[2]: *** [AudioPattern.o] Error 1
make[2]: Leaving directory `/home/h4ck3r/Desktop/wired-0.6/src/gui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/h4ck3r/Desktop/wired-0.6/src'
make: *** [all-recursive] Error 1

```      im more or less on the same boat here too,does any1 out there know what the problem may be?

---

### Post by neu2buntu on 2009-02-01
```
Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
              [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
              [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --datarootdir=DIR      read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR          read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR          info documentation [DATAROOTDIR/info]
  --localedir=DIR        locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR           man documentation [DATAROOTDIR/man]
  --docdir=DIR           documentation root [DATAROOTDIR/doc/wired]
  --htmldir=DIR          html documentation [DOCDIR]
  --dvidir=DIR           dvi documentation [DOCDIR]
  --pdfdir=DIR           pdf documentation [DOCDIR]
  --psdir=DIR            ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --enable-static[=PKGS]  build static libraries [default=no]
  --enable-shared[=PKGS]  build shared libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-debug Enable or disable debug symbol generation (default disabled)
  --enable-plugins Enable or disable Wired plugins (default enabled)
  --enable-codecs Enable or disable Wired codecs (default disabled)
  --enable-optimize Enable or disable compilation optimizations (default enabled)
  --disable-portaudio Enable or disable portaudio v19 built-in (default enabled)
  --disable-portmidi Enable or disable portmidi built-in (default enabled)
  --disable-nls           do not use Native Language Support
  --disable-rpath         do not hardcode runtime library paths

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-pic              try to use only PIC/non-PIC objects [default=use
                          both]
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-alsa (default=auto)
  --with-jack (default=auto)
  --with-oss (default=yes)
  --with-wxdir=PATH       Use uninstalled version of wxWidgets in PATH
  --with-wx-config=CONFIG wx-config script to use (optional)
  --with-wx-prefix=PREFIX Prefix where wxWidgets is installed (optional)
  --with-wx-exec-prefix=PREFIX
                          Exec prefix where wxWidgets is installed (optional)
  --with-gnu-ld           assume the C compiler uses GNU ld default=no
  --with-libiconv-prefix[=DIR]  search for libiconv in DIR/include and DIR/lib
  --without-libiconv-prefix     don't search for libiconv in includedir and libdir
  --with-included-gettext use the GNU gettext library included here
  --with-libintl-prefix[=DIR]  search for libintl in DIR/include and DIR/lib
  --without-libintl-prefix     don't search for libintl in includedir and libdir

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    C/C++/Objective C preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CXXCPP      C++ preprocessor
  PKG_CONFIG  path to pkg-config utility
  SAMPLERATE_CFLAGS
              C compiler flags for SAMPLERATE, overriding pkg-config
  SAMPLERATE_LIBS
              linker flags for SAMPLERATE, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to <wired@bloodshed.net>.
h4ck3r@h4ck3r-laptop:~/Desktop/wired-0.6$ 


```    this is the configure --help in wired

---

