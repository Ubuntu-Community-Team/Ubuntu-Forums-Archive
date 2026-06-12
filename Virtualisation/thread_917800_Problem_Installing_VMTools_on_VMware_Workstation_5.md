---
title: "Problem Installing VMTools on VMware Workstation 5.5.8"
date: 2008-09-12
forum: Virtualisation
---

### Post by The_Avenger on 2008-09-12
Hello guys,

I have a pretty good knowledge of Windows but I am new to Ubuntu and the Linux world. I am trying to run an Ubuntu installation under VMware Workstation 5.5.8 (configured expecially for Ubuntu).

I installed successfully Ubuntu 8.04 and made some basic configurations and updates. My current kernel version is 2.6.24-19-generic.

I tried to install VMware Tools but I got an error described [here]("http://muffinresearch.co.uk/archives/2008/07/13/ubuntu-hardy-setting-up-vmware-tools-from-the-cli/"). The article also suggests a solution by installing open-vmware-tools. So I downloaded them and started the ./configure as mentioned. However I get another error message which tells me that "dnet-config was not found on your PATH". According to aptitude I have libdnet installed:

p   dnet-common          - Base package for Linux DECnet
p   dnet-progs           - DECnet user programs and daemons
p   libdnet              - DECnet Libraries
p   libdnet-dev          - DECnet development libraries & Headers

Do you have any idea? Below is the whole output of the configure.

Thanks.

theavenger@UBUNTU32:~/Desktop/open-vm-tools-2008.07.01-102166$ ./configure --without-x
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking build system type... (cached) i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for pkg-config... yes
checking for X... disabled
checking for crypt in -lcrypt... yes
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for ecvt... yes
checking for fcvt... yes
checking for pthread_mutex_init in -lpthread... yes
checking for getstat in -lproc-3.2.7... yes
checking proc/sysinfo.h usability... yes
checking proc/sysinfo.h presence... yes
checking for proc/sysinfo.h... yes
checking for dumbnet-config... no
checking for dnet-config... no
configure: error: dnet-config was not found on your PATH. Please configure without dnet (using --without-dnet) or install dnet - [http://libdnet.sourceforge.net](http://libdnet.sourceforge.net)

---

### Post by Mben on 2008-09-15
You also need libdumbnet-dev

I'd also grab libnotify-dev and you'll probably be asked for libicu-dev next

---

### Post by The_Avenger on 2008-09-16
Thanks, that worked great!

Can you give me a hint how to find the correct package I need based on such an error? I could not find a hint on this one for example.

---

### Post by Mben on 2008-09-16
I don't have any really great suggestions there. In this case I figured it out with a combination of browsing in synaptic and google. Sometimes you can also get some ideas from "apt-cache search".  It also helps to be familiar with the particular library in question, but that doesn't always happen ;-)

---

### Post by The_Avenger on 2008-09-17
OK, thanks a lot for the support.

---

