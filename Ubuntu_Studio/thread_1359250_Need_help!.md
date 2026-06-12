---
title: "Need help!"
date: 2009-12-19
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2009-12-19
I'm trying to install the hdspmixer for the RME Madi card from here: [http://wiki.linuxproaudio.org/index.php/App:hpdsmixer_madi](http://wiki.linuxproaudio.org/index.php/App:hpdsmixer_madi)

I tried to follow the instructions and when I got to ./configure && make, I got this:

> ben@HMS_Audio:/usr/src/hdspmixer_madi-1.6$ sudo ./configure && make
[sudo] password for ben:                                           
checking for a BSD-compatible install... /usr/bin/install -c       
checking whether build environment is sane... yes                  
checking for gawk... gawk                                          
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
checking whether make sets $(MAKE)... (cached) yes                 
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for X... libraries , headers
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.0... found.
checking for snd_ctl_open in -lasound... yes
checking for fltk-config... /usr/bin/fltk-config
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating pixmaps/Makefile
config.status: executing depfiles commands
Making all in src
make[1]: Entering directory `/usr/src/hdspmixer_madi-1.6/src'
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"hdspmixer\" -DVERSION=\"1.6\" -DSTDC_HEADERS=1 -DHAVE_LIBASOUND=1 -I. -I.     -g -O2  -I/usr/include/freetype2 -D_THREAD_SAFE -D_REENTRANT -fno-exceptions -MT hdspmixer.o -MD -MP -MF ".deps/hdspmixer.Tpo" -c -o hdspmixer.o hdspmixer.cxx; \
        then mv -f ".deps/hdspmixer.Tpo" ".deps/hdspmixer.Po"; else rm -f ".deps/hdspmixer.Tpo"; exit 1; fi
In file included from HDSPMixerCard.h:30,
                 from hdspmixer.cxx:31:
HDSPMixerWindow.h:43:30: error: alsa/sound/hdspm.h: No such file or directory
make[1]: *** [hdspmixer.o] Error 1
make[1]: Leaving directory `/usr/src/hdspmixer_madi-1.6/src'
make: *** [all-recursive] Error 1


What in the world is this?  How do I fix it.  I don't even know where the /alsa/sound directory is.  Kernel 2.6.31-9 RT installed.  64 bit ubuntu.

Thanks,

Ben

---

### Post by Tricity on 2009-12-19
Obviously, you are missing a header file, hdspm.h - which could be part of your package or part of the Alsa system. I believe that it is part of Alsa.

try to find it:

$ locate hdspm.h


It should be at /usr/include/alsa/sound/ 

If it is not there at all, you probably need to install some dev package (not sure which, could be libclalsadev-dev)

If you find it at a different location, edit HDSPMixerWindow.h in line 43 to point at the right place. Let's assume you find the file at /usr/include/sound/hdspm.h - then you need to change the line from

#include <alsa/sound/hdspm.h>

to

#include <sound/hdspm.h>

---

### Post by pepsifx357 on 2009-12-19
Thank you very much, I will try that.

---

