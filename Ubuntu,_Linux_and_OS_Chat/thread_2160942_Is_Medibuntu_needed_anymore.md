---
title: "Is Medibuntu needed anymore?"
date: 2013-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Uncle Spellbinder on 2013-07-08
I saw a thread on another forum regarding the Medibuntu repo. Some said it was necessary, others said it's no longer needed.

Opinions?

---

### Post by 1clue on 2013-07-08
Yes and no.

You can add the medibuntu repositories to your *buntu install so no it's not.

If you care about staying legal and you live in certain countries (like USA) then you need to really understand what's involved when you load that stuff.  Also, medibuntu installs it all so you don't have to figure it all out.  So yes it is.

<soapbox>
Personally I don't see why I shouldn't be able to put a BluRay disk into my box and watch it, the same way somebody with a Windows box can do.  I don't want to copy it, or decrypt it, or share it with anyone. I just think I should be able to watch it without any fuss and without breaking any laws.
</soapbox>

---

### Post by Irihapeti on 2013-07-08
*Not a support question. Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by monkeybrain2012 on 2013-07-08
> **1clue said:**
> Yes and no.

You can add the medibuntu repositories to your *buntu install so no it's not.



:confused: If you need to add its repo than it means it is needed, no?

I guess it is still needed for new users who don't know how to compile libdvdcss and add some non free codecs (and the libav-extras libraries)

---

### Post by cariboo on 2013-07-08
The only thing I need from the medibuntu repositories is libdvdcss2, which can be installed without enabling the repositories, by using the install script located in /usr/share/doc/libdvdread. As long as I can still install the library, I don't care where it comes from, and for the most part the rest of the packages in that repository, aren't really needed any more, unless you get a thrill out of hot-babe. :-P

---

### Post by MadmanRB on 2013-07-08
Yeah but a binary is preferable to command line and compiling

---

### Post by monkeybrain2012 on 2013-07-08
> **cariboo907 said:**
> The only thing I need from the medibuntu repositories is libdvdcss2, which can be installed without enabling the repositories, by using the install script located in /usr/share/doc/libdvdread. As long as I can still install the library, I don't care where it comes from, and for the most part the rest of the packages in that repository, aren't really needed any more, unless you get a thrill out of hot-babe. :-P

  Since the script fetches libdvdcss2 from medibuntu's repository I suppose it won't work if the medibuntu repository is no longer maintained. It is quite easy for more experienced users to download the source from videolan to compile it themselves, though it may be quite intimidating for new users.

---

### Post by mc4man on 2013-07-09
When medibuntu supplied ffmpeg/libav with faac support it had some value beyond libdvdcss2 & w32codecs (w64codecs has always be a hair above worthless

At this point w32codecs isn't needed much, will be less so for general users when libav gets around to updating to 0.9.x (6 months & counting there, plus libav 9 could support fdk-aac which is better than faac & the bottom of the barrel  libvo-aacenc0

The libdvdread script will remain fine as long as the server is up & if you read the script it contains a fallback to try to compile libdvdcss if not available from medibuntu (whether that actually works don't know, don't care.

The is also a small script posted by andrew.46 that acquires, builds & installs libdvdcss2 in very short order, from a user perspective no real difference from running the dvdread script

So semi-convenient but not really needed

---

### Post by MadmanRB on 2013-07-09
yes but the end user should not have to compile, especially something that one could easily get a binary for via debian.
Remember folks: just because you like to spend hours compiling software doesnt mean everyone does, some of us actually have something called a life.

---

### Post by cariboo on 2013-07-09
I just had a look at andrew.46's instructions to build and install libdvdcss2 from source, He's set it up so that anybody that can copy and paste shouldn't have a problem making it work on their system. The instructions are [here]("http://ubuntuforums.org/showthread.php?t=2146227"). Thanks mc4man for the pointer.

---

### Post by mikodo on 2013-07-09
> **MadmanRB said:**
> yes but the end user should not have to compile, especially something that one could easily get a binary for via debian.
Remember folks: just because you like to spend hours compiling software doesnt mean everyone does, some of us actually have something called a life.
  How true. I can't seem to do both successfully. How mere casual users can do both, is a bit of an enigma to me. I keep saying I am going to spend less time learning how to do new stuff and just use my computer for daily tasks and spend more time doing the other life tasks. But, after I have learned what I think I need to know in linux, what do I do? I look for the next think to learn. It's not a hobby, it's an addiction. I have other addictions that I have come to grips with by not "using", (booze and smoking), but I don't want to do this with computers. I know many people are just computer hobbyists.  I struggle with finding a happy medium, and I am not prepared to quit "using" my computer just yet. It is a quandary.

So, now I can compile things if I need like libdvdcss from [VideoLan]("http://www.videolan.org/developers/libdvdcss.html") if I want and it is really easy, but only because I stole time from other responsibilities to take the time to learn. Now, I am seeing things like the script pointed out by cariboo907 in /usr/share/doc/libdvdread and other scripts, and I want to start messing with them now. I see no end in sight, if I don't take the initiative and curtail my time with linux.

Software is great fun. But 5 years into it at 60 years of age, it is taking too much of my time to learn. Where was it when I was 15 and had a lot more time, energy, health and marbles rolling around in my head? I guess I need to be happy with what I have. I am grateful for the people before me that have made Linux easy for me to use.

I apologize for hi-jacking this thread for my personal blog, with repeated edits.  MadmanRB's comments, struck a nerve that I needed to think about, and putting it out in type is the easiest way for me to make myself be thoughtful, about whatever.

---

### Post by MadmanRB on 2013-07-09
indeed, I myself am a normal user at heart, I should not have to compile.

---

### Post by mc4man on 2013-07-10
> **MadmanRB said:**
> indeed, I myself am a normal user at heart, I should not have to compile.
Nobody is 'asking' you or anyone else to 'have' to compile anything. 
Atm the servers are up, even if they disappeared it just simply a matter of copy & paste which I think most users can handle.
Worst case the current dvdread script can be redone.

As an example here I replaced the current script with Andrew's - no changes at all, only running the well known command
Took about 25 sec's to complete the whole process - 
```
doug@doug-XPS-M1330:~$ [COLOR="#0000CD"]/usr/share/doc/libdvdread4/install-css.sh[/COLOR]
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter2 libavutil-dev libdrm2:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
mkdir: created directory &#8216;/home/doug/libdvdcss_build&#8217;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libdvdcss2' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter2 libavutil-dev libdrm2:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
--2013-07-10 13:18:52--  [http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2](http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 338588 (331K) [text/plain]
Saving to: &#8216;libdvdcss-1.2.13.tar.bz2&#8217;

100%[==============================================================================>] 338,588      433KB/s   in 0.8s   

2013-07-10 13:18:53 (433 KB/s) - &#8216;libdvdcss-1.2.13.tar.bz2&#8217; saved [338588/338588]

libdvdcss-1.2.13/
libdvdcss-1.2.13/src/
libdvdcss-1.2.13/src/dvdcss/
libdvdcss-1.2.13/src/dvdcss/dvdcss.h
libdvdcss-1.2.13/src/libdvdcss.pc.in
libdvdcss-1.2.13/src/device.c
libdvdcss-1.2.13/src/error.c
libdvdcss-1.2.13/src/ioctl.h
libdvdcss-1.2.13/src/device.h
libdvdcss-1.2.13/src/css.h
libdvdcss-1.2.13/src/common.h
libdvdcss-1.2.13/src/csstables.h
libdvdcss-1.2.13/src/ioctl.c
libdvdcss-1.2.13/src/libdvdcss.c
libdvdcss-1.2.13/src/libdvdcss.h
libdvdcss-1.2.13/src/css.c
libdvdcss-1.2.13/README
libdvdcss-1.2.13/aclocal.m4
libdvdcss-1.2.13/configure
libdvdcss-1.2.13/config.h.in
libdvdcss-1.2.13/depcomp
libdvdcss-1.2.13/test/
libdvdcss-1.2.13/test/dvd_region.c
libdvdcss-1.2.13/test/csstest.c
libdvdcss-1.2.13/config.sub
libdvdcss-1.2.13/config.guess
libdvdcss-1.2.13/AUTHORS
libdvdcss-1.2.13/libdvdcss.spec
libdvdcss-1.2.13/NEWS
libdvdcss-1.2.13/Makefile.am
libdvdcss-1.2.13/doc/
libdvdcss-1.2.13/doc/doxygen.cfg.in
libdvdcss-1.2.13/doc/footer.html
libdvdcss-1.2.13/doc/header.html
libdvdcss-1.2.13/COPYING
libdvdcss-1.2.13/INSTALL
libdvdcss-1.2.13/configure.ac
libdvdcss-1.2.13/ChangeLog
libdvdcss-1.2.13/missing
libdvdcss-1.2.13/m4/
libdvdcss-1.2.13/m4/ltsugar.m4
libdvdcss-1.2.13/m4/lt~obsolete.m4
libdvdcss-1.2.13/m4/libtool.m4
libdvdcss-1.2.13/m4/attributes.m4
libdvdcss-1.2.13/m4/ltversion.m4
libdvdcss-1.2.13/m4/ltoptions.m4
libdvdcss-1.2.13/install-sh
libdvdcss-1.2.13/ltmain.sh
libdvdcss-1.2.13/Makefile.in
libdvdcss-1.2.13/msvc/
libdvdcss-1.2.13/msvc/libdvdcss.dsp
libdvdcss-1.2.13/msvc/workspace.dsw
libdvdcss-1.2.13/msvc/csstest.dsp
libdvdcss-1.2.13/msvc/config.h
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking whether make supports nested variables... yes
checking how to print strings... printf
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking whether O_BINARY is declared... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for posix mkdir()... yes
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking sys/dvdio.h usability... no
checking sys/dvdio.h presence... no
checking for sys/dvdio.h... no
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking dvd.h usability... no
checking dvd.h presence... no
checking for dvd.h... no
checking sys/scsi/scsi_types.h, usability... no
checking sys/scsi/scsi_types.h, presence... no
checking for sys/scsi/scsi_types.h,... no
checking sys/scsi.h usability... no
checking sys/scsi.h presence... no
checking for sys/scsi.h... no
checking IOKit/storage/IODVDMediaBSDClient.h usability... no
checking IOKit/storage/IODVDMediaBSDClient.h presence... no
checking for IOKit/storage/IODVDMediaBSDClient.h... no
checking if gcc supports -Wall flag... yes
checking if gcc supports -Wsign-compare flag... yes
checking for gcc way to treat warnings as errors... -Werror
checking if gcc supports -fvisibility=hidden... yes
checking if gcc supports __attribute__(( visibility("default") ))... yes
checking for doxygen... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/doxygen.cfg
config.status: creating src/libdvdcss.pc
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
make  all-am
make[1]: Entering directory `/home/doug/libdvdcss_build/libdvdcss-1.2.13'
  CC     src/libdvdcss.lo
src/libdvdcss.c: In function 'dvdcss_open':
src/libdvdcss.c:419:18: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
             write( i_fd, psz_tag, strlen(psz_tag) );
                  ^
  CC     src/device.lo
  CC     src/css.lo
src/css.c: In function '_dvdcss_title':
src/css.c:275:18: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
             write( i_fd, psz_key, KEY_SIZE * 3 + 1 );
                  ^
  CC     src/ioctl.lo
  CC     src/error.lo
  CCLD   libdvdcss.la
make[1]: Leaving directory `/home/doug/libdvdcss_build/libdvdcss-1.2.13'

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@doug-XPS-M1330 ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ libdvdcss2 ]
3 -  Version: [ 1.2.13 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ libdvdcss-1.2.13 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ libdvdcss2 ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make[1]: Entering directory `/home/doug/libdvdcss_build/libdvdcss-1.2.13'
 /bin/mkdir -p '/usr/local/lib'
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   libdvdcss.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libdvdcss.so.2.1.0 /usr/local/lib/libdvdcss.so.2.1.0
libtool: install: (cd /usr/local/lib && { ln -s -f libdvdcss.so.2.1.0 libdvdcss.so.2 || { rm -f libdvdcss.so.2 && ln -s libdvdcss.so.2.1.0 libdvdcss.so.2; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libdvdcss.so.2.1.0 libdvdcss.so || { rm -f libdvdcss.so && ln -s libdvdcss.so.2.1.0 libdvdcss.so; }; })
libtool: install: /usr/bin/install -c .libs/libdvdcss.lai /usr/local/lib/libdvdcss.la
libtool: install: /usr/bin/install -c .libs/libdvdcss.a /usr/local/lib/libdvdcss.a
libtool: install: chmod 644 /usr/local/lib/libdvdcss.a
libtool: install: ranlib /usr/local/lib/libdvdcss.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/mkdir -p '/usr/local/share/doc/libdvdcss'
 /usr/bin/install -c -m 644 AUTHORS COPYING NEWS README ChangeLog '/usr/local/share/doc/libdvdcss'
 /bin/mkdir -p '/usr/local/lib/pkgconfig'
 /usr/bin/install -c -m 644 src/libdvdcss.pc '/usr/local/lib/pkgconfig'
 /bin/mkdir -p '/usr/local/include/dvdcss'
 /usr/bin/install -c -m 644 src/dvdcss/dvdcss.h '/usr/local/include/dvdcss'
make[1]: Leaving directory `/home/doug/libdvdcss_build/libdvdcss-1.2.13'

======================== Installation successful ==========================

Copying documentation directory...
./
./doc/
./doc/header.html
./doc/doxygen.cfg
./doc/footer.html
./doc/doxygen.cfg.in
./COPYING
./NEWS
./ChangeLog
./AUTHORS
./README
./INSTALL

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Transferring package to /home/doug/libdvdcss_build...OK

Erasing temporary files...OK

Deleting doc-pak directory...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/doug/libdvdcss_build/libdvdcss2_1.2.13-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r libdvdcss2

**********************************************************************

test -z "libdvdcss.la" || rm -f libdvdcss.la
rm -f "./so_locations"
rm -rf .libs _libs
rm -rf src/.libs src/_libs
rm -Rf stamp-doxygen doc/html
rm -f *.o
rm -f src/css.o
rm -f src/css.lo
rm -f src/device.o
rm -f src/device.lo
rm -f src/dvd_region-ioctl.o
rm -f src/error.o
rm -f src/error.lo
rm -f src/ioctl.o
rm -f src/ioctl.lo
rm -f src/libdvdcss.o
rm -f src/libdvdcss.lo
rm -f test/csstest-csstest.o
rm -f test/dvd_region-dvd_region.o
rm -f *.lo
rm -f *.tab.c
test -z "doc/doxygen.cfg src/libdvdcss.pc" || rm -f doc/doxygen.cfg src/libdvdcss.pc
test . = "." || test -z "" || rm -f 
rm -f src/.deps/.dirstamp
rm -f src/.dirstamp
rm -f test/.deps/.dirstamp
rm -f test/.dirstamp
test -z "ChangeLog" || rm -f ChangeLog
rm -f config.h stamp-h1
rm -f libtool config.lt
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
rm -f config.status config.cache config.log configure.lineno config.status.lineno
rm -rf src/.deps test/.deps
rm -f Makefile
doug@doug-XPS-M1330:~$ 
```

---

### Post by monkeybrain2012 on 2013-07-10
Looking at the bright side libdvdcss2 is really easy compile so it would be great boost of confidence for the new user when he/she compiles something the first time and gets an easy success. :)

The commands for compiling libdvdcss2 are actually easier and less cryptic than the commands for adding medibuntu (see instructions here. [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php))

The only problem is that the new user would most likely not know about Andrew's tutorial.

---

### Post by monkeybrain2012 on 2013-07-10
> **mikodo said:**
> 

Software is great fun. But 5 years into it at 60 years of age, it is taking too much of my time to learn. Where was it when I was 15 and had a lot more time, energy, health and marbles rolling around in my head? I guess I need to be happy with what I have. I am grateful for the people before me that have made Linux easy for me to use.
.

Actually Ubuntu is still really easy comparing to some distros which are really for masochists. I have Debian on another partition.. basically almost NOTHING works out of the box (touchpad, wifi, bluetooth) without tweaking config files, installing firmware etc. These are only things that are expected not to work OOTB for various reasons, I have not even talked about bugs On the same machine Ubuntu (and Fedora as well) works out of the box for all of these.

---

### Post by Erik1984 on 2013-07-10
> **MadmanRB said:**
> yes but the end user should not have to compile, especially something that one could easily get a binary for via debian.
Remember folks: just because you like to spend hours compiling software doesnt mean everyone does, some of us actually have something called a life.

I don't have a life and still don't like compiling :P

---

### Post by mc4man on 2013-07-11
> **Euroman said:**
> I don't have a life and still don't like compiling :P
There is a significant difference between a user activly participating in  compiling/installing a source & just simply running a single command &  nothing more.
Can't even begin to find a problem here.

---

### Post by cariboo on 2013-07-11
> **mc4man said:**
> There is a significant difference between a user activly participating in  compiling/installing a source & just simply running a single command &  nothing more.
Can't even begin to find a problem here.

I have to agree, but I think to many users, the command is a magic incantation, that they find hard to understand. :-P

---

### Post by MadmanRB on 2013-07-11
Well mainly new users, I dont think we should force compiling on them

---

