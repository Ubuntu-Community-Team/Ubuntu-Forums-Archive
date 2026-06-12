---
title: "why is it so difficult?"
date: 2009-10-29
forum: Testimonials &amp; Experiences
---

### Post by whtemple1959 on 2009-10-29
Hello,
 

 After working with Ubuntu for some weeks now I have found why Linux will never become the dominate force in Operating Systems.
 

 One must be a “rocket scientist' or at the least a “programmer” to use it.
 

 I want to do few things things...1) rip my CDs to MP3 and migrate those to my Sansa, 20 chat with my newborn's grandparents via web cam similar to Yahoo, 3) manage my finances and pay bills, 4) use an “office suite” that works.
 

 I have been trying to get some Nursery Rythmns onto my Sansa to play for my child and below are the  errors I get..... I do not understand... If an application “REQUIRES” pieces and parts why are they not included in the download?
 

 Can some one explain why when I tried to rip a CD using Asunder it stated I needed LAME? Or when I tried to play an MP3 Rhytmnbox states I need a plugin ID3 tag demuxer?
 

 And I have had similar problems with Empathy always asking for dependant applications.
 

 Should I just go to the synaptic manager and install everything?
 

 I believe the community as a whole should hire a real world user to assure ease of use and then a marketable product might be developed.
 

 I know I will get grief...I read about it on a help page that linux people do not like newbies...but hey as they say “that's life”
 

 I look forward to seeing if things get simpler in the future.
 

 Thanks,
 Bill
 

 william@william-desktop:~/rhythmbox-0.12.5$ ./configure 
 checking for a BSD-compatible install... /usr/bin/install -c 
 checking whether build environment is sane... yes 
 checking for a thread-safe mkdir -p... /bin/mkdir -p 
 checking for gawk... no 
 checking for mawk... mawk 
 checking whether make sets $(MAKE)... yes 
 checking whether to enable maintainer-specific portions of Makefiles... no 
 checking whether NLS is requested... yes 
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
 checking for intltool >= 0.35.0... ./configure: line 4542: intltool-update: command not found 
  found 
 configure: error: Your intltool is too old.  You need intltool 0.35.0 or later. 



**Went and installed intltool...**


 william@william-desktop:~/rhythmbox-0.12.5$ ./configure 
 checking for a BSD-compatible install... /usr/bin/install -c 
 checking whether build environment is sane... yes 
 checking for a thread-safe mkdir -p... /bin/mkdir -p 
 checking for gawk... no 
 checking for mawk... mawk 
 checking whether make sets $(MAKE)... yes 
 checking whether to enable maintainer-specific portions of Makefiles... no 
 checking whether NLS is requested... yes 
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
 checking for intltool >= 0.35.0... 0.40.6 found 
 checking for intltool-update... /usr/bin/intltool-update 
 checking for intltool-merge... /usr/bin/intltool-merge 
 checking for intltool-extract... /usr/bin/intltool-extract 
 checking for xgettext... /usr/bin/xgettext 
 checking for msgmerge... /usr/bin/msgmerge 
 checking for msgfmt... /usr/bin/msgfmt 
 checking for gmsgfmt... /usr/bin/msgfmt 
 checking for perl... /usr/bin/perl 
 checking for perl >= 5.8.1... 5.10.0 
 checking for XML::Parser... ok 
 checking for library containing strerror... none required 
 checking for gcc... (cached) gcc 
 checking whether we are using the GNU C compiler... (cached) yes 
 checking whether gcc accepts -g... (cached) yes 
 checking for gcc option to accept ISO C89... (cached) none needed 
 checking dependency style of gcc... (cached) gcc3 
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
 checking how to run the C preprocessor... gcc -E 
 checking for grep that handles long lines and -e... /bin/grep 
 checking for egrep... /bin/grep -E 
 checking for ANSI C header files... yes 
 checking build system type... i686-pc-linux-gnu 
 checking host system type... i686-pc-linux-gnu 
 checking for a sed that does not truncate output... /bin/sed 
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
 checking for objdump... objdump 
 checking how to recognize dependent libraries... pass_all 
 checking for ar... ar 
 checking for strip... strip 
 checking for ranlib... ranlib 
 checking command to parse /usr/bin/nm -B output from gcc object... ok 
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
 checking whether we are using the GNU C++ compiler... (cached) no 
 checking whether g++ accepts -g... (cached) no 
 checking dependency style of g++... (cached) none 
 checking for objdir... .libs 
 checking if gcc supports -fno-rtti -fno-exceptions... no 
 checking for gcc option to produce PIC... -fPIC -DPIC 
 checking if gcc PIC flag -fPIC -DPIC works... yes 
 checking if gcc static flag -static works... yes 
 checking if gcc supports -c -o file.o... yes 
 checking if gcc supports -c -o file.o... (cached) yes 
 checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes 
 checking whether -lc should be explicitly linked in... no 
 checking dynamic linker characteristics... GNU/Linux ld.so 
 checking how to hardcode library paths into programs... immediate 
 checking whether stripping libraries is possible... yes 
 checking if libtool supports shared libraries... yes 
 checking whether to build shared libraries... yes 
 checking whether to build static libraries... yes 
 configure: creating ./config.lt 
 config.lt: creating libtool 
 checking whether byte ordering is bigendian... no 
 checking size of long... 4 
 checking for GNU extension fwrite_unlocked... yes 
 checking for mkdtemp... yes 
 checking for pkg-config... /usr/bin/pkg-config 
 checking pkg-config is at least version 0.9.0... yes 
 checking for RB_CLIENT... configure: error: Package requirements (glib-2.0 >= 2.16.0 gio-2.0 >= 2.16.0) were not met: 
  
 No package 'glib-2.0' found 
 No package 'gio-2.0' found 
  
 Consider adjusting the PKG_CONFIG_PATH environment variable if you 
 installed software in a non-standard prefix. 
  
 Alternatively, you may set the environment variables RB_CLIENT_CFLAGS 
 and RB_CLIENT_LIBS to avoid the need to call pkg-config. 
 See the pkg-config man page for more details. 



**Installed glib but could not find gio...**


  
 william@william-desktop:~/rhythmbox-0.12.5$ ./configure 
 checking for a BSD-compatible install... /usr/bin/install -c 
 checking whether build environment is sane... yes 
 checking for a thread-safe mkdir -p... /bin/mkdir -p 
 checking for gawk... no 
 checking for mawk... mawk 
 checking whether make sets $(MAKE)... yes 
 checking whether to enable maintainer-specific portions of Makefiles... no 
 checking whether NLS is requested... yes 
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
 checking for intltool >= 0.35.0... 0.40.6 found 
 checking for intltool-update... /usr/bin/intltool-update 
 checking for intltool-merge... /usr/bin/intltool-merge 
 checking for intltool-extract... /usr/bin/intltool-extract 
 checking for xgettext... /usr/bin/xgettext 
 checking for msgmerge... /usr/bin/msgmerge 
 checking for msgfmt... /usr/bin/msgfmt 
 checking for gmsgfmt... /usr/bin/msgfmt 
 checking for perl... /usr/bin/perl 
 checking for perl >= 5.8.1... 5.10.0 
 checking for XML::Parser... ok 
 checking for library containing strerror... none required 
 checking for gcc... (cached) gcc 
 checking whether we are using the GNU C compiler... (cached) yes 
 checking whether gcc accepts -g... (cached) yes 
 checking for gcc option to accept ISO C89... (cached) none needed 
 checking dependency style of gcc... (cached) gcc3 
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
 checking how to run the C preprocessor... gcc -E 
 checking for grep that handles long lines and -e... /bin/grep 
 checking for egrep... /bin/grep -E 
 checking for ANSI C header files... yes 
 checking build system type... i686-pc-linux-gnu 
 checking host system type... i686-pc-linux-gnu 
 checking for a sed that does not truncate output... /bin/sed 
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
 checking for objdump... objdump 
 checking how to recognize dependent libraries... pass_all 
 checking for ar... ar 
 checking for strip... strip 
 checking for ranlib... ranlib 
 checking command to parse /usr/bin/nm -B output from gcc object... ok 
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
 checking whether we are using the GNU C++ compiler... (cached) no 
 checking whether g++ accepts -g... (cached) no 
 checking dependency style of g++... (cached) none 
 checking for objdir... .libs 
 checking if gcc supports -fno-rtti -fno-exceptions... no 
 checking for gcc option to produce PIC... -fPIC -DPIC 
 checking if gcc PIC flag -fPIC -DPIC works... yes 
 checking if gcc static flag -static works... yes 
 checking if gcc supports -c -o file.o... yes 
 checking if gcc supports -c -o file.o... (cached) yes 
 checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes 
 checking whether -lc should be explicitly linked in... no 
 checking dynamic linker characteristics... GNU/Linux ld.so 
 checking how to hardcode library paths into programs... immediate 
 checking whether stripping libraries is possible... yes 
 checking if libtool supports shared libraries... yes 
 checking whether to build shared libraries... yes 
 checking whether to build static libraries... yes 
 configure: creating ./config.lt 
 config.lt: creating libtool 
 checking whether byte ordering is bigendian... no 
 checking size of long... 4 
 checking for GNU extension fwrite_unlocked... yes 
 checking for mkdtemp... yes 
 checking for pkg-config... /usr/bin/pkg-config 
 checking pkg-config is at least version 0.9.0... yes 
 checking for RB_CLIENT... yes 



**And** **what does all of this mean....**


 checking for RHYTHMBOX... configure: error: Package requirements (		  gtk+-2.0 >= 2.12.0					  glib-2.0 >= 2.16.0  gio-2.0 >= 2.16.0					  gio-unix-2.0 >= 2.16.0				  gnome-media-profiles >= 2.8 		  libsoup-2.4 >= 2.26.0				  libsoup-gnome-2.4 >= 2.26.0  libgnomeui-2.0) were not met: 
  
 No package 'gtk+-2.0' found 
 No package 'gnome-media-profiles' found 
 No package 'libsoup-2.4' found 
 No package 'libsoup-gnome-2.4' found 
 No package 'libgnomeui-2.0' found 
  
 Consider adjusting the PKG_CONFIG_PATH environment variable if you 
 installed software in a non-standard prefix. 
  
 Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS 
 and RHYTHMBOX_LIBS to avoid the need to call pkg-config. 
 See the pkg-config man page for more details.

---

### Post by P4man on 2009-10-29
My car is so hard to start. I open the hood, open the electrical circuit, reading the carshop manual I cant figure out wich pins to short so it will start! I guess no one told me I should just turn the ignition key ;)

Dont install your software by compiling it, just run add/remove programs, select the programs you want, click apply. Done, ready. works. easy :)

---

### Post by P4man on 2009-10-29
BTW if for some reason you want the latest version of rhythbox, grab the package here:
[http://www.getdeb.net/app/Rhythmbox](http://www.getdeb.net/app/Rhythmbox)

Download the appropriate .deb, double click, apply done

---

### Post by snowpine on 2009-10-29
1. Rhythmbox is already pre-installed in Ubuntu... You are wasting your time :) .... Applications -> Sound & Video !

2. The mp3 codec cannot be legally distributed in all countries, so Ubuntu doesn't ship with it... does Windows? Mac? Anyways, the following terminal command will give you lots of yummy codecs:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by alphaniner on 2009-10-29
```
If an application “REQUIRES” pieces and parts why are they not included in the download?
```

With audio and video stuff the reason is often legal.  Stuff like mp3 and DVD requires proprietary software to 'use.'

---

### Post by aysiu on 2009-10-29
> **whtemple1959 said:**
> 
 After working with Ubuntu for some weeks now I have found why Linux will never become the dominate force in Operating Systems.
 

 One must be a &#8220;rocket scientist' or at the least a &#8220;programmer&#8221; to use it.
 
 I believe the community as a whole should hire a real world user to assure ease of use and then a marketable product might be developed. I'm neither a rocket scientist nor a programmer, and not only do I use Ubuntu, but I also am able to write tutorials to help others use it.

So your statement is patently false.

If you want help, ask nicely for it in a support thread. No need to make untrue statements.

---

### Post by philinux on 2009-10-29
To the OP. 

Your bean count says 1. Why have you been struggling with all this and not asked here before you tear you hair out.

Also Post one problem per thread. Much easier to respond.

Click the RestrictedFormats and Medibuntu link below and follow the instructions there.

In case you're wondering why you have to do this, legal reasons, then read here.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

