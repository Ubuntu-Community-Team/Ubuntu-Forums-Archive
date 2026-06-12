---
title: "Wiinstrument Won't Install"
date: 2009-12-26
forum: Ubuntu Studio
---

### Post by thelethargarian on 2009-12-26
I am trying to install Wiinstrument ([http://screenfashion.org/releases/the_wiinstrument/](http://screenfashion.org/releases/the_wiinstrument/)) on my laptop running Xubuntu 9.10 64 bit. It configured fine with 
```

./configure

``` printing out this 
```

[checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands

```, but when I run 
```

make

```, it comes up with this error 
```

make  all-recursive
make[1]: Entering directory `/home/username/Downloads/wiinstrument'
Making all in src
make[2]: Entering directory `/home/username/Downloads/wiinstrument/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../../lib/drums -I. -I../../lib    -I../fmodapi/api/inc -Wall -I/usr/include/pango-1.0    -I/usr/include/freetype2 -I/usr/include/glib-2.0    -I/usr/lib/glib-2.0/include -I/usr/lib/ruby/1.8/i486-linux -fPIC    -DBOOST_DISABLE_THREADS -g -O2 -MT CoreConfiiguration.o -MD -MP -MF ".deps/CoreConfiiguration.Tpo" -c -o CoreConfiiguration.o CoreConfiiguration.cpp; \
    then mv -f ".deps/CoreConfiiguration.Tpo" ".deps/CoreConfiiguration.Po"; else rm -f ".deps/CoreConfiiguration.Tpo"; exit 1; fi
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:44:29: error: boost/utility.hpp: No such file or directory
./Core.hpp:45:34: error: boost/lexical_cast.hpp: No such file or directory
./Core.hpp:46:32: error: boost/scoped_ptr.hpp: No such file or directory
./Core.hpp:47:32: error: boost/shared_ptr.hpp: No such file or directory
./Core.hpp:49:26: error: Gosu/Audio.hpp: No such file or directory
./Core.hpp:50:27: error: Gosu/Bitmap.hpp: No such file or directory
./Core.hpp:51:26: error: Gosu/Color.hpp: No such file or directory
./Core.hpp:52:32: error: Gosu/Directories.hpp: No such file or directory
./Core.hpp:53:25: error: Gosu/Font.hpp: No such file or directory
./Core.hpp:54:26: error: Gosu/Image.hpp: No such file or directory
./Core.hpp:55:26: error: Gosu/Input.hpp: No such file or directory
./Core.hpp:56:23: error: Gosu/IO.hpp: No such file or directory
./Core.hpp:57:25: error: Gosu/Math.hpp: No such file or directory
./Core.hpp:58:25: error: Gosu/Text.hpp: No such file or directory
./Core.hpp:59:27: error: Gosu/Timing.hpp: No such file or directory
./Core.hpp:60:27: error: Gosu/Window.hpp: No such file or directory
./Core.hpp:61:29: error: Gosu/Graphics.hpp: No such file or directory
./Core.hpp:62:29: error: Gosu/Platform.hpp: No such file or directory
./Core.hpp:63:28: error: Gosu/Utility.hpp: No such file or directory
In file included from ./Core.hpp:66,
                 from CoreConfiiguration.cpp:35:
./MoteInput.hpp:44:27: error: boost/array.hpp: No such file or directory
./MoteInput.hpp:45:37: error: boost/circular_buffer.hpp: No such file or directory
In file included from ./Core.hpp:67,
                 from CoreConfiiguration.cpp:35:
./SimpleGui.hpp:47:30: error: boost/function.hpp: No such file or directory
./SimpleGui.hpp:48:26: error: boost/bind.hpp: No such file or directory
In file included from ./Core.hpp:67,
                 from CoreConfiiguration.cpp:35:
./SimpleGui.hpp:223: warning: ignoring #pragma mark GUI
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:174: warning: ignoring #pragma mark GUI
./Core.hpp:203: warning: ignoring #pragma mark Additional
./Core.hpp:209: warning: ignoring #pragma mark Confiiguration
./Core.hpp:233: warning: ignoring #pragma mark DrumStiicks
./Core.hpp:251: warning: ignoring #pragma mark DrumStiicksSampler
./Core.hpp:270: warning: ignoring #pragma mark Kiiboard
CoreConfiiguration.cpp:36:19: error: Utils.h: No such file or directory
CoreConfiiguration.cpp:37:28: error: boost/format.hpp: No such file or directory
In file included from ./Core.hpp:65,
                 from CoreConfiiguration.cpp:35:
./MidiOutput.hpp:49: error: ‘boost’ has not been declared
./MidiOutput.hpp:49: error: expected ‘{’ before ‘noncopyable’
./MidiOutput.hpp:50: error: invalid type in declaration before ‘{’ token
./MidiOutput.hpp:50: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
./MidiOutput.hpp:51: error: expected primary-expression before ‘public’
./MidiOutput.hpp:51: error: expected ‘}’ before ‘public’
./MidiOutput.hpp:51: error: expected ‘,’ or ‘;’ before ‘public’
./MidiOutput.hpp:53: error: expected unqualified-id before ‘const’
./MidiOutput.hpp:53: error: expected ‘)’ before ‘const’
./MidiOutput.hpp:54: error: expected constructor, destructor, or type conversion before ‘;’ token
./MidiOutput.hpp:59: error: ‘boost’ was not declared in this scope
./MidiOutput.hpp:59: error: template argument 1 is invalid
./MidiOutput.hpp:59: error: template argument 2 is invalid
./MidiOutput.hpp:59: error: invalid type in declaration before ‘;’ token
./MidiOutput.hpp:60: error: ‘boost’ was not declared in this scope
./MidiOutput.hpp:60: error: template argument 1 is invalid
./MidiOutput.hpp:60: error: template argument 2 is invalid
./MidiOutput.hpp:60: error: expected initializer before ‘MidiDeviceIterator’
./MidiOutput.hpp:62: error: ‘boost’ has not been declared
./MidiOutput.hpp:62: error: expected ‘{’ before ‘noncopyable’
./MidiOutput.hpp:63: error: invalid type in declaration before ‘{’ token
./MidiOutput.hpp:63: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
./MidiOutput.hpp:64: error: expected primary-expression before ‘public’
./MidiOutput.hpp:64: error: expected ‘}’ before ‘public’
./MidiOutput.hpp:64: error: expected ‘,’ or ‘;’ before ‘public’
./MidiOutput.hpp:66: error: expected constructor, destructor, or type conversion before ‘;’ token
./MidiOutput.hpp:70: error: non-member function ‘void noteOn(int, int)’ cannot have cv-qualifier
./MidiOutput.hpp:71: error: non-member function ‘void noteOff(int)’ cannot have cv-qualifier
./MidiOutput.hpp:72: error: non-member function ‘void allNotesOff()’ cannot have cv-qualifier
./MidiOutput.hpp:73: error: non-member function ‘void control(int, int)’ cannot have cv-qualifier
./MidiOutput.hpp:76: error: ‘boost’ has not been declared
./MidiOutput.hpp:76: error: expected constructor, destructor, or type conversion before ‘<’ token
./MidiOutput.hpp:88: error: expected unqualified-id before ‘private’
./MidiOutput.hpp:91: error: expected declaration before ‘}’ token
make[2]: *** [CoreConfiiguration.o] Error 1
make[2]: Leaving directory `/home/username/Downloads/wiinstrument/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/username/Downloads/wiinstrument'
make: *** [all] Error 2

```. I tried this howto: [http://ubuntuforums.org/showthread.php?t=866322&highlight=wiinstrument](http://ubuntuforums.org/showthread.php?t=866322&highlight=wiinstrument),but it didn't work either. I just don't know why. The error seems to say that it is missing a lot of files in src/. I see that there used to be a .deb package on getdeb ([https://bugs.launchpad.net/getdeb.net/+bug/240654](https://bugs.launchpad.net/getdeb.net/+bug/240654)), but the link is broken. Thanks for any help you can give. I think it would be sweet to use the wiimote as a midi controller.

---

### Post by Stochastic on 2009-12-27
It looks like the files that can't be found are from the libboost dev library.  If you're running Karmic, try installing the package [libboost1.38-dev]("apt:libboost1.38-dev")

---

### Post by thelethargarian on 2009-12-27
Thanks, but it didn't quite solve the error completely...
```

make

```now returns
```

make  all-recursive
make[1]: Entering directory `/home/username/Downloads/wiinstrument'
Making all in src
make[2]: Entering directory `/home/username/Downloads/wiinstrument/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../../lib/drums -I. -I../../lib    -I../fmodapi/api/inc -Wall -I/usr/include/pango-1.0    -I/usr/include/freetype2 -I/usr/include/glib-2.0    -I/usr/lib/glib-2.0/include -I/usr/lib/ruby/1.8/i486-linux -fPIC    -DBOOST_DISABLE_THREADS -g -O2 -MT CoreConfiiguration.o -MD -MP -MF ".deps/CoreConfiiguration.Tpo" -c -o CoreConfiiguration.o CoreConfiiguration.cpp; \
    then mv -f ".deps/CoreConfiiguration.Tpo" ".deps/CoreConfiiguration.Po"; else rm -f ".deps/CoreConfiiguration.Tpo"; exit 1; fi
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:49:26: error: Gosu/Audio.hpp: No such file or directory
./Core.hpp:50:27: error: Gosu/Bitmap.hpp: No such file or directory
./Core.hpp:51:26: error: Gosu/Color.hpp: No such file or directory
./Core.hpp:52:32: error: Gosu/Directories.hpp: No such file or directory
./Core.hpp:53:25: error: Gosu/Font.hpp: No such file or directory
./Core.hpp:54:26: error: Gosu/Image.hpp: No such file or directory
./Core.hpp:55:26: error: Gosu/Input.hpp: No such file or directory
./Core.hpp:56:23: error: Gosu/IO.hpp: No such file or directory
./Core.hpp:57:25: error: Gosu/Math.hpp: No such file or directory
./Core.hpp:58:25: error: Gosu/Text.hpp: No such file or directory
./Core.hpp:59:27: error: Gosu/Timing.hpp: No such file or directory
./Core.hpp:60:27: error: Gosu/Window.hpp: No such file or directory
./Core.hpp:61:29: error: Gosu/Graphics.hpp: No such file or directory
./Core.hpp:62:29: error: Gosu/Platform.hpp: No such file or directory
./Core.hpp:63:28: error: Gosu/Utility.hpp: No such file or directory
In file included from ./Core.hpp:67,
                 from CoreConfiiguration.cpp:35:
./SimpleGui.hpp:223: warning: ignoring #pragma mark GUI
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:174: warning: ignoring #pragma mark GUI
./Core.hpp:203: warning: ignoring #pragma mark Additional
./Core.hpp:209: warning: ignoring #pragma mark Confiiguration
./Core.hpp:233: warning: ignoring #pragma mark DrumStiicks
./Core.hpp:251: warning: ignoring #pragma mark DrumStiicksSampler
./Core.hpp:270: warning: ignoring #pragma mark Kiiboard
CoreConfiiguration.cpp:36:19: error: Utils.h: No such file or directory
In file included from ./Core.hpp:67,
                 from CoreConfiiguration.cpp:35:
./SimpleGui.hpp:80: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:80: error: expected &#8216;)&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:95: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:95: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:107: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:107: error: ISO C++ forbids declaration of &#8216;Graphics&#8217; with no type
./SimpleGui.hpp:107: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:114: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:114: error: ISO C++ forbids declaration of &#8216;Font&#8217; with no type
./SimpleGui.hpp:114: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./SimpleGui.hpp:147: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:147: error: expected &#8216;)&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:170: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:170: error: expected &#8216;)&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:191: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:191: error: expected &#8216;)&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:192: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:192: error: expected &#8216;)&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:213: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:213: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:229: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:229: error: ISO C++ forbids declaration of &#8216;Font&#8217; with no type
./SimpleGui.hpp:229: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SimpleGui.hpp:230: error: &#8216;Gosu&#8217; has not been declared
./SimpleGui.hpp:230: error: ISO C++ forbids declaration of &#8216;Font&#8217; with no type
./SimpleGui.hpp:230: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:104: error: &#8216;Gosu&#8217; has not been declared
./Core.hpp:104: error: expected &#8216;)&#8217; before &#8216;&&#8217; token
./Core.hpp:118: error: &#8216;Gosu&#8217; has not been declared
./Core.hpp:118: error: ISO C++ forbids declaration of &#8216;Graphics&#8217; with no type
./Core.hpp:118: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./Core.hpp:119: error: &#8216;Gosu&#8217; has not been declared
./Core.hpp:119: error: ISO C++ forbids declaration of &#8216;Audio&#8217; with no type
./Core.hpp:119: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./Core.hpp:121: error: &#8216;Gosu&#8217; has not been declared
./Core.hpp:121: error: ISO C++ forbids declaration of &#8216;Font&#8217; with no type
./Core.hpp:121: error: expected &#8216;;&#8217; before &#8216;smallestFont&#8217;
./Core.hpp:207: error: &#8216;Gosu&#8217; has not been declared
./Core.hpp:207: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;color&#8217;
./Core.hpp:290: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:290: error: template argument 1 is invalid
./Core.hpp:291: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:291: error: template argument 1 is invalid
./Core.hpp:292: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:292: error: template argument 1 is invalid
./Core.hpp:293: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:293: error: template argument 1 is invalid
./Core.hpp:294: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:294: error: template argument 1 is invalid
./Core.hpp:295: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:295: error: template argument 1 is invalid
./Core.hpp:296: error: &#8216;Gosu&#8217; was not declared in this scope
./Core.hpp:296: error: template argument 1 is invalid
./Core.hpp:170: warning: non-static const member &#8216;const std::wstring Wiinstrument::Core::noteNames [12]&#8217; in class without a constructor
CoreConfiiguration.cpp: In member function &#8216;void Wiinstrument::Core::initializeConfiigurationGui()&#8217;:
CoreConfiiguration.cpp:44: error: &#8216;graphics&#8217; was not declared in this scope
CoreConfiiguration.cpp:51: error: &#8216;Gosu&#8217; has not been declared
CoreConfiiguration.cpp:64: error: &#8216;bigFont&#8217; was not declared in this scope
CoreConfiiguration.cpp:141: error: &#8216;smallestFont&#8217; was not declared in this scope
CoreConfiiguration.cpp: In member function &#8216;void Wiinstrument::Core::drawConfiigurationBackground()&#8217;:
CoreConfiiguration.cpp:280: error: &#8216;glPushMatrix&#8217; was not declared in this scope
CoreConfiiguration.cpp:285: error: &#8216;glPopMatrix&#8217; was not declared in this scope
CoreConfiiguration.cpp: In member function &#8216;void Wiinstrument::Core::drawConfiiguration()&#8217;:
CoreConfiiguration.cpp:329: error: &#8216;smallestFont&#8217; was not declared in this scope
make[2]: *** [CoreConfiiguration.o] Error 1
make[2]: Leaving directory `/home/username/Downloads/wiinstrument/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/username/Downloads/wiinstrument'
make: *** [all] Error 2

```

---

### Post by AutoStatic on 2009-12-27
> * Linux

To get The Wiinstrument running under Linux, install the following libraries via
your favorite package manager or by hand:

glew (glew.sourceforge.net)
libpng ([www.libpng.org](www.libpng.org))
zlib ([www.zlib.net](www.zlib.net))
fmod 3 ([www.fmod.com](www.fmod.com))
boost ([www.boost.org](www.boost.org))
Gosu ([http://www.raschke.de/julian/gosu/](http://www.raschke.de/julian/gosu/))
portmidi ([http://www.cs.cmu.edu/~music/portmusic/portmidi/](http://www.cs.cmu.edu/~music/portmusic/portmidi/))
CWiid ([http://abstrakraft.org/cwiid/](http://abstrakraft.org/cwiid/))

Then change into the Wiinstrument project directory and type:

./configure
make
make install
You need Gosu, there's no package of it apparently so you need it to compile it yourself.

---

### Post by thelethargarian on 2009-12-27
Better now that I installed Gosu, but now
```

make

```
returns
```

make  all-recursive
make[1]: Entering directory `/home/username/Downloads/wiinstrument'
Making all in src
make[2]: Entering directory `/home/username/Downloads/wiinstrument/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../../lib/drums -I. -I../../lib    -I../fmodapi/api/inc -Wall -I/usr/include/pango-1.0    -I/usr/include/freetype2 -I/usr/include/glib-2.0    -I/usr/lib/glib-2.0/include -I/usr/lib/ruby/1.8/i486-linux -fPIC    -DBOOST_DISABLE_THREADS -g -O2 -MT CoreConfiiguration.o -MD -MP -MF ".deps/CoreConfiiguration.Tpo" -c -o CoreConfiiguration.o CoreConfiiguration.cpp; \
    then mv -f ".deps/CoreConfiiguration.Tpo" ".deps/CoreConfiiguration.Po"; else rm -f ".deps/CoreConfiiguration.Tpo"; exit 1; fi
In file included from ./Core.hpp:67,
                 from CoreConfiiguration.cpp:35:
./SimpleGui.hpp:223: warning: ignoring #pragma mark GUI
In file included from ./Core.hpp:82,
                 from CoreConfiiguration.cpp:35:
./LinuxMoteInput.hpp:52:2: warning: #import is a deprecated GCC extension
./LinuxMoteInput.hpp:53:2: warning: #import is a deprecated GCC extension
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:174: warning: ignoring #pragma mark GUI
./Core.hpp:203: warning: ignoring #pragma mark Additional
./Core.hpp:209: warning: ignoring #pragma mark Confiiguration
./Core.hpp:233: warning: ignoring #pragma mark DrumStiicks
./Core.hpp:251: warning: ignoring #pragma mark DrumStiicksSampler
./Core.hpp:270: warning: ignoring #pragma mark Kiiboard
CoreConfiiguration.cpp:36:19: error: Utils.h: No such file or directory
./LinuxMoteInput.hpp:63: warning: &#8216;Wiinstrument::pt2Object&#8217; defined but not used
make[2]: *** [CoreConfiiguration.o] Error 1
make[2]: Leaving directory `/home/username/Downloads/wiinstrument/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/username/Downloads/wiinstrument'
make: *** [all] Error 2

```

---

### Post by Stochastic on 2009-12-28
Okay, I'm going to attempt to teach you how to fish rather than just handing you a sushi roll to eat.

The warning messages on a compile can usually be ignored (unless you're involved in coding the application or patches to it).  So your latest fatal error message you got was ```
CoreConfiiguration.cpp:36:19: error: Utils.h: No such file or directory
```

The 'No such file or directory' error usually means that either 1) you are missing some file/libraries that the program builds against or 2) the code of the program has a typo.  In most cases it's number 1.

To find a library or package that contains a particular file, I always use the [apt-file]("apt:apt-file") program.  It's run by this command ```
apt-file search filename
```
and when Utils.h is used as the filename, a massive list is given back.  We're only looking for files that have just 'Utils.h' as the file's exact name, so we can narrow the search by including the forwardslash of the higher directory ```
apt-file search /Utils.h
```
This returns a much shorter list to sort through.  It's likely that the package/file you're looking for in this case in in the /usr/include directory structure, so we can filter that last command down further with ```
apt-file search /Utils.h | grep /usr/include
```

From there I'll let you sort out which one is the culprit (or you can always e-mail the developers of that app, quite often they like to be notified of compilation troubles on popular distros).

---

### Post by anakiller on 2010-08-06
Helle everybody, I have the same problem and I don't know how to resolve it!
```
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/boost/  wiinstrument/src/ -r
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/Gosu/ wiinstrument/src/ -r
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/Gosu/gcc/* wiinstrument/src/
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/portmidi/* wiinstrument/src/
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/glew/* wiinstrument/src/ -r
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/drums/* wiinstrument/src/
anael@anael-desktop:~/Desktop$ cp wiinstrument/lib/libcwiid/* wiinstrument/src/
anael@anael-desktop:~/Desktop$ cd wiinstrument
anael@anael-desktop:~/Desktop/wiinstrument$ make
 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/anael/Desktop/wiinstrument'
Making all in src
make[2]: Entering directory `/home/anael/Desktop/wiinstrument/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../../lib/drums -I. -I../../lib    -I../fmodapi/api/inc -Wall -I/usr/include/pango-1.0	-I/usr/include/freetype2 -I/usr/include/glib-2.0	-I/usr/lib/glib-2.0/include -I/usr/lib/ruby/1.8/i486-linux -fPIC	-DBOOST_DISABLE_THREADS -g -O2 -MT CoreConfiiguration.o -MD -MP -MF ".deps/CoreConfiiguration.Tpo" -c -o CoreConfiiguration.o CoreConfiiguration.cpp; \
	then mv -f ".deps/CoreConfiiguration.Tpo" ".deps/CoreConfiiguration.Po"; else rm -f ".deps/CoreConfiiguration.Tpo"; exit 1; fi
In file included from ./Core.hpp:67,
                 from CoreConfiiguration.cpp:35:
./SimpleGui.hpp:223: warning: ignoring #pragma mark GUI
In file included from ./Core.hpp:82,
                 from CoreConfiiguration.cpp:35:
./LinuxMoteInput.hpp:52:2: warning: #import is a deprecated GCC extension
./LinuxMoteInput.hpp:53:2: warning: #import is a deprecated GCC extension
In file included from CoreConfiiguration.cpp:35:
./Core.hpp:174: warning: ignoring #pragma mark GUI
./Core.hpp:203: warning: ignoring #pragma mark Additional
./Core.hpp:209: warning: ignoring #pragma mark Confiiguration
./Core.hpp:233: warning: ignoring #pragma mark DrumStiicks
./Core.hpp:251: warning: ignoring #pragma mark DrumStiicksSampler
./Core.hpp:270: warning: ignoring #pragma mark Kiiboard
In file included from ./boost/circular_buffer.hpp:62,
                 from ./MoteInput.hpp:45,
                 from ./Core.hpp:66,
                 from CoreConfiiguration.cpp:35:
./boost/circular_buffer/base.hpp:116: error: declaration of ‘typedef class boost::reverse_iterator<boost::cb_details::iterator<boost::circular_buffer<T, Alloc>, boost::cb_details::nonconst_traits<Alloc> > > boost::circular_buffer<T, Alloc>::reverse_iterator’
./boost/iterator/reverse_iterator.hpp:23: error: changes meaning of ‘reverse_iterator’ from ‘class boost::reverse_iterator<boost::cb_details::iterator<boost::circular_buffer<T, Alloc>, boost::cb_details::nonconst_traits<Alloc> > >’
./boost/bind/placeholders.hpp:56: warning: ‘<unnamed>::_3’ defined but not used
./boost/bind/placeholders.hpp:57: warning: ‘<unnamed>::_4’ defined but not used
./boost/bind/placeholders.hpp:58: warning: ‘<unnamed>::_5’ defined but not used
./boost/bind/placeholders.hpp:59: warning: ‘<unnamed>::_6’ defined but not used
./boost/bind/placeholders.hpp:60: warning: ‘<unnamed>::_7’ defined but not used
./boost/bind/placeholders.hpp:61: warning: ‘<unnamed>::_8’ defined but not used
./boost/bind/placeholders.hpp:62: warning: ‘<unnamed>::_9’ defined but not used
./LinuxMoteInput.hpp:63: warning: ‘Wiinstrument::pt2Object’ defined but not used
make[2]: *** [CoreConfiiguration.o] Error 1
make[2]: Leaving directory `/home/anael/Desktop/wiinstrument/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/anael/Desktop/wiinstrument'
make: *** [all] Error 2

``` Does anyone can help me?

---

