---
title: "Medibuntu repositories closing"
date: 2013-09-12
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-09-12
As noted [here]("http://gauvain.pocentek.net/node/61"), Medibuntu is going down shortly after Saucy is released. So if you need anything in the repository you better get it soon.

Personally I only use Medibuntu for libdvdcss. [Jonathan RIddell ]("http://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan")has taken over maintaining libdvdcss, which will be available directly from [Videolan]("http://www.videolan.org/index.html").

---

### Post by kostkon on 2013-09-12
RIP. It served us well.

I only used it in the past for w32codecs, but now gst and ffmpeg more or less can play almost anything, and many Windows audio and video codecs of the past are not in use anymore, while libdvdcss' maintenance has been handed over already to others; so I think we will survive this..

---

### Post by coffeecat on 2013-09-13
> **cariboo907 said:**
> [Jonathan RIddell ](http://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan)has taken over maintaining libdvdcss, which will be available directly from [Videolan]("http://www.videolan.org/index.html").

Do you know whether anyone is picking up the ball with regard to /usr/share/doc/libdvdread4/install-css.sh? Whether or not this is rewritten for Saucy and beyond, if it's not updated in earlier releases we're going to have many support threads for failed install-css.sh runs. Instructions to use install-css.sh are on a few Ubuntu wiki pages and more than a few home-grown howto and blog sites.

---

### Post by ventrical on 2013-09-13
I am curious if this will affect Ubuntu Studio also?

---

### Post by mc4man on 2013-09-13
> **coffeecat said:**
> Do you know whether anyone is picking up the ball with regard to /usr/share/doc/libdvdread4/install-css.sh? Whether or not this is rewritten for Saucy and beyond, if it's not updated in earlier releases we're going to have many support threads for failed install-css.sh runs. Instructions to use install-css.sh are on a few Ubuntu wiki pages and more than a few home-grown howto and blog sites.
[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928)
Changed already  in saucy, SRU's for other releases that may or may not occur

---

### Post by coffeecat on 2013-09-13
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928)
Changed already  in saucy, SRU's for other releases that may or may not occur

Good news, thanks. The last post seems to imply that an SRU for supported older releases will be available - we shall see.

---

### Post by |{urse on 2013-09-13
Haha, when I saw this I said "libdvdcss, noooooooo!!" aloud until I read the first post, lol, thx for the infos. :shock:

---

### Post by QDR06VV9 on 2013-09-13
> **ventrical said:**
> I am curious if this will affect Ubuntu Studio also?

Me Also?

---

### Post by ventrical on 2013-09-13
> **runrickus said:**
> Me Also?


dvdstyler and kino need that ffmpeg. Ubuntu Studio does not use libdvdcss.  At least it's not in the repos. So who knows ?

---

### Post by Yellow Pasque on 2013-09-13
> Ubuntu Studio does not use libdvdcss.
Ubuntu Studio handles libdvdcss install just like the other Ubuntu derivatives: [https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs](https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs)
..which means that once the install script gets fixed in older versions, the medibuntu closure will be transparent to users.

> dvdstyler and kino need that ffmpeg
ffmpeg/libav-extra packages are now available in the main repos.

---

### Post by QDR06VV9 on 2013-09-13
> **Temüjin said:**
> Ubuntu Studio handles libdvdcss install just like the other Ubuntu derivatives: [https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs](https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs)
..which means that once the install script gets fixed in older versions, the medibuntu closure will be transparent to users.


ffmpeg/libav-extra packages are now available in the main repos.

Good Info, Thanks Temujin!

---

### Post by ventrical on 2013-09-14
+1 :)

---

### Post by andrew.46 on 2013-09-20
Hmmm..... does this still work?

[http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448](http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448)

---

### Post by xc3RnbFO8P on 2013-09-21
> **andrew.46 said:**
> Hmmm..... does this still work?

[http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448](http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448)

Yes it works in 12.04 and solves this problem:
> libdvdread: Unable to read VTS_TMAPT
(I cant test it in 13.10, no dvd drive)

---

### Post by andrew.46 on 2013-09-21
> **Ringi said:**
> Yes it works in 12.04  [...]

Thanks for having a look :)

---

### Post by Yellow Pasque on 2013-09-21
> **andrew.46 said:**
> Hmmm..... does this still work? [http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448](http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448)
:?
Sure, it works, but I'm not sure why Ubuntu users would build from source instead of using the install script to grab the appropriate package from [http://download.videolan.org/pub/debian/](http://download.videolan.org/pub/debian/)

---

### Post by cariboo on 2013-09-21
> **Temüjin said:**
> :?
Sure, it works, but I'm not sure why Ubuntu users would build from source instead of using the install script to grab the appropriate package from [http://download.videolan.org/pub/debian/](http://download.videolan.org/pub/debian/)

Running the script doesn't take any user intervention after you copy/paste it and enter your password, so aside from installing some needed libraries if they aren't installed already, it's just like running the script in /usr/share/doc/libdvdread4. As a matter of act, it may be easier for many to do the copy/paste, as quite a few users have no idea how to navigate to anything outside of the home directory.

---

### Post by ibjsb4 on 2013-09-22
Can I now use the .deb package thats in my home folder to install it on other computers?

---

### Post by Yellow Pasque on 2013-09-22
> **cariboo907 said:**
> As a matter of act, it may be easier for many to do the copy/paste, as quite a few users have no idea how to navigate to anything outside of the home directory.

You don't need to navigate outside of the home dir. The one-line command is given with full path on the very popular RestricedFormat page, so I still don't see any advantage to doing it Gentoo style :P
[https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs](https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs)
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by andrew.46 on 2013-09-23
> **Temüjin said:**
> :?
Sure, it works, but I'm not sure why Ubuntu users would build from source instead of using the install script to grab the appropriate package from [http://download.videolan.org/pub/debian/](http://download.videolan.org/pub/debian/)

It is just another choice :)

---

### Post by mc4man on 2013-09-26
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928)
Changed already  in saucy, SRU's for other releases that may or may not occur

All of the current Ubuntu releases now have the new dvdread & script, most in *-proposed

---

### Post by xc3RnbFO8P on 2013-09-28
> **Ringi said:**
> Yes it works in 12.04 and solves this problem:

(I cant test it in 13.10, no dvd drive)

Tested in 13.10

```
rig@rig-Aspire-R3600:~$ sudo apt-get -y install build-essential checkinstall && \
> mkdir -pv $HOME/libdvdcss_build && cd $HOME/libdvdcss_build && \
> sudo apt-get remove libdvdcss2 && \
> wget http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2 && \
> tar xvf libdvdcss-1.2.13.tar.bz2 && \
> cd libdvdcss-1.2.13 && \
> ./configure && make && \
> sudo checkinstall --pakdir "$HOME/libdvdcss_build" --backup=no --deldoc=yes \
>                   --pkgname libdvdcss2 --pkgversion "1.2.13" --fstrans=no \
>                   --deldesc=yes --delspec=yes --default && \
> make distclean && sudo ldconfig
[sudo] password for rig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 121 kB of archives.
After this operation, 516 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ saucy/universe checkinstall amd64 1.6.2-4ubuntu1 [121 kB]
Fetched 121 kB in 0s (382 kB/s)  
Selecting previously unselected package checkinstall.
(Reading database ... 911634 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.2-4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up checkinstall (1.6.2-4ubuntu1) ...
mkdir: created directory ‘/home/rig/libdvdcss_build’
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libdvdcss2' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2013-09-28 13:13:12--  http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 338588 (331K) [text/plain]
Saving to: ‘libdvdcss-1.2.13.tar.bz2’

100%[======================================>] 338.588      529KB/s   in 0,6s   

2013-09-28 13:13:13 (529 KB/s) - ‘libdvdcss-1.2.13.tar.bz2’ saved [338588/338588]

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
checking for gawk... gawk
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
make[1]: Entering directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'
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
make[1]: Leaving directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@rig-Aspire-R3600 ]
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
make[1]: Entering directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'
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
make[1]: Leaving directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'

======================== Installation successful ==========================

Copying documentation directory...
./
./doc/
./doc/footer.html
./doc/header.html
./doc/doxygen.cfg.in
./doc/doxygen.cfg
./COPYING
./ChangeLog
./README
./INSTALL
./AUTHORS
./NEWS

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Transferring package to /home/rig/libdvdcss_build...OK

Erasing temporary files...OK

Deleting doc-pak directory...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/rig/libdvdcss_build/libdvdcss2_1.2.13-1_amd64.deb

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
rig@rig-Aspire-R3600:~/libdvdcss_build/libdvdcss-1.2.13$ 

```

---

### Post by euanbuntu2 on 2013-10-10
Hey, with this videolan site, we need something called Git to get libdvdcss. I'm quite new to ubuntu and don't want to mess it up. Could someone please walk me through what on earth I need to do to get dvd playback on 13.04 please?

---

### Post by euanbuntu2 on 2013-10-10
> **Ringi said:**
> Tested in 13.10

```
rig@rig-Aspire-R3600:~$ sudo apt-get -y install build-essential checkinstall && \
> mkdir -pv $HOME/libdvdcss_build && cd $HOME/libdvdcss_build && \
> sudo apt-get remove libdvdcss2 && \
> wget http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2 && \
> tar xvf libdvdcss-1.2.13.tar.bz2 && \
> cd libdvdcss-1.2.13 && \
> ./configure && make && \
> sudo checkinstall --pakdir "$HOME/libdvdcss_build" --backup=no --deldoc=yes \
>                   --pkgname libdvdcss2 --pkgversion "1.2.13" --fstrans=no \
>                   --deldesc=yes --delspec=yes --default && \
> make distclean && sudo ldconfig
[sudo] password for rig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 121 kB of archives.
After this operation, 516 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ saucy/universe checkinstall amd64 1.6.2-4ubuntu1 [121 kB]
Fetched 121 kB in 0s (382 kB/s)  
Selecting previously unselected package checkinstall.
(Reading database ... 911634 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.2-4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up checkinstall (1.6.2-4ubuntu1) ...
mkdir: created directory ‘/home/rig/libdvdcss_build’
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libdvdcss2' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2013-09-28 13:13:12--  http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 338588 (331K) [text/plain]
Saving to: ‘libdvdcss-1.2.13.tar.bz2’

100%[======================================>] 338.588      529KB/s   in 0,6s   

2013-09-28 13:13:13 (529 KB/s) - ‘libdvdcss-1.2.13.tar.bz2’ saved [338588/338588]

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
checking for gawk... gawk
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
make[1]: Entering directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'
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
make[1]: Leaving directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@rig-Aspire-R3600 ]
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
make[1]: Entering directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'
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
make[1]: Leaving directory `/home/rig/libdvdcss_build/libdvdcss-1.2.13'

======================== Installation successful ==========================

Copying documentation directory...
./
./doc/
./doc/footer.html
./doc/header.html
./doc/doxygen.cfg.in
./doc/doxygen.cfg
./COPYING
./ChangeLog
./README
./INSTALL
./AUTHORS
./NEWS

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Transferring package to /home/rig/libdvdcss_build...OK

Erasing temporary files...OK

Deleting doc-pak directory...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/rig/libdvdcss_build/libdvdcss2_1.2.13-1_amd64.deb

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
rig@rig-Aspire-R3600:~/libdvdcss_build/libdvdcss-1.2.13$ 

```


I just tried that and got this:

christmaspudding@Christmas:~$ sudo apt-get -y install build-essential checkinstall && \
> > mkdir -pv $HOME/libdvdcss_build && cd $HOME/libdvdcss_build && \
> > sudo apt-get remove libdvdcss2 && \
> > wget [http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2](http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2) && \
> > tar xvf libdvdcss-1.2.13.tar.bz2 && \
> > cd libdvdcss-1.2.13 && \
> > ./configure && make && \
> > sudo checkinstall --pakdir "$HOME/libdvdcss_build" --backup=no --deldoc=yes \
> >                   --pkgname libdvdcss2 --pkgversion "1.2.13" --fstrans=no \
> >                   --deldesc=yes --delspec=yes --default && \
> > make distclean && sudo ldconfig
[sudo] password for christmaspudding: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libstdc++6-4.7-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  libstdc++6-4.7-doc
The following NEW packages will be installed
  build-essential checkinstall dpkg-dev g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6 MB of archives.
After this operation, 30.0 MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libstdc++6-4.7-dev amd64 4.7.3-1ubuntu1 [1,704 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main g++-4.7 amd64 4.7.3-1ubuntu1 [7,993 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main g++ amd64 4:4.7.3-1ubuntu10 [1,448 B]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main dpkg-dev all 1.16.10ubuntu1 [712 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main build-essential amd64 11.6ubuntu4 [5,672 B]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/universe checkinstall amd64 1.6.2-4ubuntu1 [121 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 10.6 MB in 6s (1,544 kB/s)                                             
Selecting previously unselected package libstdc++6-4.7-dev:amd64.
(Reading database ... 229036 files and directories currently installed.)
Unpacking libstdc++6-4.7-dev:amd64 (from .../libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.6ubuntu4_amd64.deb) ...
Selecting previously unselected package checkinstall.
Unpacking checkinstall (from .../checkinstall_1.6.2-4ubuntu1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Setting up libstdc++6-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up g++-4.7 (4.7.3-1ubuntu1) ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up dpkg-dev (1.16.10ubuntu1) ...
Setting up build-essential (11.6ubuntu4) ...
Setting up checkinstall (1.6.2-4ubuntu1) ...
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
No command '-pv' found, did you mean:
 Command 'pv' from package 'pv' (universe)
-pv: command not found

---

### Post by xc3RnbFO8P on 2013-10-10
Install from synaptic Package Manager  :
make 
automake

---

### Post by Yellow Pasque on 2013-10-10
> **euanbuntu2 said:**
> Hey, with this videolan site, we need something called Git to get libdvdcss. I'm quite new to ubuntu and don't want to mess it up. Could someone please walk me through what on earth I need to do to get dvd playback on 13.04 please?


You don't need git. Just get the appropriate libdvdcss2 .deb package for your architecture and install it: [http://download.videolan.org/pub/debian/raring/](http://download.videolan.org/pub/debian/raring/)

---

### Post by JMB74 on 2013-10-10
The package **libdvdread4** includes a script **/usr/share/doc/libdvdread4/install-css.sh** that automates the download and install from the videolan site.

---

### Post by craig10x on 2013-10-10
Yes...just go to the link Temujin just provided and select the deb package for libdvdcss2 (64 bit or 32 bit depending on what your computer has)...once you download the deb, go to the downloads section of your file manager and you will see it...right click and select the option to open with ubuntu software center which will install it for you...the other file you need (libdvdread4) is already installed on your system when you downloaded ubuntu restricted extras...

---

### Post by Yellow Pasque on 2013-10-10
> **JMB74 said:**
> The package **libdvdread4** includes a script **/usr/share/doc/libdvdread4/install-css.sh** that automates the download and install from the videolan site.

Yes, but unless you enable the proposed repo to get the updated package, the install-css.sh script still points to medibuntu.

---

### Post by JMB74 on 2013-10-10
The updated package is in "release" for saucy [https://launchpad.net/ubuntu/+source/libdvdread/4.2.0+20130219-2ubuntu2](https://launchpad.net/ubuntu/+source/libdvdread/4.2.0+20130219-2ubuntu2)

---

### Post by Yellow Pasque on 2013-10-10
> **JMB74 said:**
> The updated package is in "release" for saucy [https://launchpad.net/ubuntu/+source/libdvdread/4.2.0+20130219-2ubuntu2](https://launchpad.net/ubuntu/+source/libdvdread/4.2.0+20130219-2ubuntu2)

Yes, but my comment was directed at euanbuntu2, who is not using saucy.

---

### Post by JMB74 on 2013-10-10
You were replying to me, and this is the ubuntu+1 (saucy) forum last time I checked.

Anyway, no matter. It is there for saucy and will presumably be so for raring at some point not too distant.

---

### Post by euanbuntu2 on 2013-10-10
So does that mean that dvd's are defunct in raring for now?

I'm confused.

If anyone could walk me through step by step what I might have to do to get things working I'd be very grateful.

If I need to do terminal stuff, please could you let me know exactly what I need to type in there as I'm fairly new at this

---

### Post by cariboo on 2013-10-10
You can use andrew.46's script [here]("http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448"). To use it, just copy the script, and paste it in a terminal and press enter, it will do the rest for you.

---

### Post by Yellow Pasque on 2013-10-11
> **euanbuntu2 said:**
> So does that mean that dvd's are defunct in raring for now?

No. Did you follow the instructions I gave you previously (and craig10x detailed nicely)?

---

### Post by speartip on 2013-10-20
You could just download the libdvdcss2 .deb package from here:
[http://download.videolan.org/ubuntu/saucy/](http://download.videolan.org/ubuntu/saucy/)
Once installed dvds playback fine.

---

### Post by coffeecat on 2013-10-20
Closed.

U+1 is for the discussion/troubleshooting of the development version of Ubuntu, now 14.04.

If anyone has any problem or question following the closure of medibuntu, please post in the regular support forums. The install-css.sh script should now point to videolan in updated installations of all currently supported versions of Ubuntu.

---

