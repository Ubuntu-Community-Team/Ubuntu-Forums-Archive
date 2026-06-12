---
title: "Hit a wall w/ snort install"
date: 2011-07-29
forum: Security
---

### Post by sdmike6 on 2011-07-29
I'm running Ubuntu 11.04 x64

I'm going through the installation guide from snort and I hit a wall at the end on the installation notes.

The problem is that I can't configure daq0.5

This is the output I receive: 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for objdump... objdump
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
checking whether to build static libraries... yes
checking for visibility support... yes
checking CFLAGS for gcc -Wall... -Wall
checking CFLAGS for gcc -Wwrite-strings... -Wwrite-strings
checking CFLAGS for gcc -Wsign-compare... -Wsign-compare
checking CFLAGS for gcc -Wcast-align... -Wcast-align
checking CFLAGS for gcc -Wextra... -Wextra
checking CFLAGS for gcc -Wformat... -Wformat
checking CFLAGS for gcc -Wformat-security... -Wformat-security
checking CFLAGS for gcc -Wno-unused-parameter... -Wno-unused-parameter
checking CFLAGS for gcc -fno-strict-aliasing... -fno-strict-aliasing
checking CFLAGS for gcc -fdiagnostics-show-option... -fdiagnostics-show-option
checking CFLAGS for gcc -pedantic -std=c99 -D_GNU_SOURCE... -pedantic -std=c99 -D_GNU_SOURCE
checking for getaddrinfo... yes
checking for flex... flex
checking for flex 2.4 or higher... yes
checking for bison... bison
checking linux/if_ether.h usability... yes
checking linux/if_ether.h presence... yes
checking for linux/if_ether.h... yes
checking linux/if_packet.h usability... yes
checking linux/if_packet.h presence... yes
checking for linux/if_packet.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking dnet.h usability... no
checking dnet.h presence... no
checking for dnet.h... no
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking libipq.h usability... no
checking libipq.h presence... no
checking for libipq.h... no
checking for linux/netfilter.h... yes
checking for dnet.h... (cached) no
checking for netinet/in.h... (cached) yes
checking libnetfilter_queue/libnetfilter_queue.h usability... no
checking libnetfilter_queue/libnetfilter_queue.h presence... no
checking for libnetfilter_queue/libnetfilter_queue.h... no
checking for linux/netfilter.h... (cached) yes
checking for pcap.h... (cached) yes
checking for pcap_lib_version... checking for pcap_lib_version in -lpcap... yes
checking for libpcap version >= "1.0.0"... yes
checking for dlopen in -ldl... yes
checking for inttypes.h... (cached) yes
checking for memory.h... (cached) yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking for netinet/in.h... (cached) yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for inline... inline
checking for size_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for gethostbyname... yes
checking for getpagesize... (cached) yes
checking for memset... yes
checking for munmap... yes
checking for socket... yes
checking for strchr... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtoul... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating api/Makefile
config.status: creating os-daq-modules/Makefile
config.status: creating sfbpf/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

Build AFPacket DAQ module.. : yes
Build Dump DAQ module...... : yes
Build IPFW DAQ module...... : yes
Build IPQ DAQ module....... : no
Build NFQ DAQ module....... : no
Build PCAP DAQ module...... : yes

```

---

### Post by emiller12345 on 2011-07-29
did you download libdnet from:
```
http://code.google.com/p/libdnet/ 

```
you can download a copy with 
```
svn checkout **[B]*http***[/B]://libdnet.googlecode.com/svn/trunk/ libdnet-read-only
```
I didn't have much luck with the different repos versions of libdnet.  The google one has worked well in the past.

---

### Post by sdmike6 on 2011-08-01
So I went to install libdnet and I can't even get a make file from that.

I'm using a fresh install of Ubuntu server and I'm following the snort guide step by step.

Are there some hidden dependencies I'm not seeing here and that are not mentioned in the snort guide?

Here's my output when I'm configuring the make file:

```
libdnet-1.12/
libdnet-1.12/acconfig.h
libdnet-1.12/aclocal.m4
libdnet-1.12/config/
libdnet-1.12/config/acinclude.m4
libdnet-1.12/config/config.guess
libdnet-1.12/config/config.sub
libdnet-1.12/config/install-sh
libdnet-1.12/config/ltmain.sh
libdnet-1.12/config/missing
libdnet-1.12/config/mkinstalldirs
libdnet-1.12/configure
libdnet-1.12/configure.in
libdnet-1.12/dnet-config.in
libdnet-1.12/include/
libdnet-1.12/include/config.h.in
libdnet-1.12/include/dnet/
libdnet-1.12/include/dnet/addr.h
libdnet-1.12/include/dnet/arp.h
libdnet-1.12/include/dnet/blob.h
libdnet-1.12/include/dnet/eth.h
libdnet-1.12/include/dnet/fw.h
libdnet-1.12/include/dnet/icmp.h
libdnet-1.12/include/dnet/intf.h
libdnet-1.12/include/dnet/ip.h
libdnet-1.12/include/dnet/ip6.h
libdnet-1.12/include/dnet/Makefile.am
libdnet-1.12/include/dnet/Makefile.in
libdnet-1.12/include/dnet/os.h
libdnet-1.12/include/dnet/rand.h
libdnet-1.12/include/dnet/route.h
libdnet-1.12/include/dnet/tcp.h
libdnet-1.12/include/dnet/tun.h
libdnet-1.12/include/dnet/udp.h
libdnet-1.12/include/dnet.h
libdnet-1.12/include/err.h
libdnet-1.12/include/Makefile.am
libdnet-1.12/include/Makefile.in
libdnet-1.12/include/queue.h
libdnet-1.12/include/stamp-h.in
libdnet-1.12/INSTALL
libdnet-1.12/libdnet.spec
libdnet-1.12/LICENSE
libdnet-1.12/Makefile.am
libdnet-1.12/Makefile.am.common
libdnet-1.12/Makefile.in
libdnet-1.12/man/
libdnet-1.12/man/dnet.3
libdnet-1.12/man/Makefile.am
libdnet-1.12/man/Makefile.in
libdnet-1.12/python/
libdnet-1.12/python/dnet.c
libdnet-1.12/python/dnet.pyx
libdnet-1.12/python/Makefile.am
libdnet-1.12/python/Makefile.in
libdnet-1.12/python/pyrex.diff
libdnet-1.12/python/setup.py.in
libdnet-1.12/python/test.py
libdnet-1.12/README
libdnet-1.12/src/
libdnet-1.12/src/addr-util.c
libdnet-1.12/src/addr.c
libdnet-1.12/src/arp-bsd.c
libdnet-1.12/src/arp-ioctl.c
libdnet-1.12/src/arp-none.c
libdnet-1.12/src/arp-win32.c
libdnet-1.12/src/blob.c
libdnet-1.12/src/err.c
libdnet-1.12/src/eth-bsd.c
libdnet-1.12/src/eth-dlpi.c
libdnet-1.12/src/eth-linux.c
libdnet-1.12/src/eth-ndd.c
libdnet-1.12/src/eth-none.c
libdnet-1.12/src/eth-pfilt.c
libdnet-1.12/src/eth-snoop.c
libdnet-1.12/src/eth-win32.c
libdnet-1.12/src/fw-ipchains.c
libdnet-1.12/src/fw-ipf.c
libdnet-1.12/src/fw-ipfw.c
libdnet-1.12/src/fw-none.c
libdnet-1.12/src/fw-pf.c
libdnet-1.12/src/fw-pktfilter.c
libdnet-1.12/src/intf-win32.c
libdnet-1.12/src/intf.c
libdnet-1.12/src/ip-cooked.c
libdnet-1.12/src/ip-util.c
libdnet-1.12/src/ip-win32.c
libdnet-1.12/src/ip.c
libdnet-1.12/src/ip6.c
libdnet-1.12/src/Makefile.am
libdnet-1.12/src/Makefile.in
libdnet-1.12/src/memcmp.c
libdnet-1.12/src/rand.c
libdnet-1.12/src/route-bsd.c
libdnet-1.12/src/route-hpux.c
libdnet-1.12/src/route-linux.c
libdnet-1.12/src/route-none.c
libdnet-1.12/src/route-win32.c
libdnet-1.12/src/strlcat.c
libdnet-1.12/src/strlcpy.c
libdnet-1.12/src/strsep.c
libdnet-1.12/src/tun-bsd.c
libdnet-1.12/src/tun-linux.c
libdnet-1.12/src/tun-none.c
libdnet-1.12/src/tun-solaris.c
libdnet-1.12/test/
libdnet-1.12/test/check/
libdnet-1.12/test/check/check_addr.c
libdnet-1.12/test/check/check_arp.c
libdnet-1.12/test/check/check_blob.c
libdnet-1.12/test/check/check_eth.c
libdnet-1.12/test/check/check_fw.c
libdnet-1.12/test/check/check_intf.c
libdnet-1.12/test/check/check_ip.c
libdnet-1.12/test/check/check_rand.c
libdnet-1.12/test/check/check_route.c
libdnet-1.12/test/check/Makefile.am
libdnet-1.12/test/check/Makefile.in
libdnet-1.12/test/dnet/
libdnet-1.12/test/dnet/addr.c
libdnet-1.12/test/dnet/arp.c
libdnet-1.12/test/dnet/aton.c
libdnet-1.12/test/dnet/aton.h
libdnet-1.12/test/dnet/dnet.8
libdnet-1.12/test/dnet/dnet.c
libdnet-1.12/test/dnet/eth.c
libdnet-1.12/test/dnet/fw.c
libdnet-1.12/test/dnet/hex.c
libdnet-1.12/test/dnet/icmp.c
libdnet-1.12/test/dnet/intf.c
libdnet-1.12/test/dnet/ip.c
libdnet-1.12/test/dnet/Makefile.am
libdnet-1.12/test/dnet/Makefile.in
libdnet-1.12/test/dnet/mod.h
libdnet-1.12/test/dnet/rand.c
libdnet-1.12/test/dnet/route.c
libdnet-1.12/test/dnet/send.c
libdnet-1.12/test/dnet/tcp.c
libdnet-1.12/test/dnet/udp.c
libdnet-1.12/test/Makefile.am
libdnet-1.12/test/Makefile.in
libdnet-1.12/THANKS
libdnet-1.12/TODO
libdnet-1.12/trunk/
libdnet-1.12/trunk/acconfig.h
libdnet-1.12/trunk/aclocal.m4
libdnet-1.12/trunk/config/
libdnet-1.12/trunk/config/acinclude.m4
libdnet-1.12/trunk/config/config.guess
libdnet-1.12/trunk/config/config.sub
libdnet-1.12/trunk/config/install-sh
libdnet-1.12/trunk/config/libtool.m4
libdnet-1.12/trunk/config/ltmain.sh
libdnet-1.12/trunk/config/missing
libdnet-1.12/trunk/config/mkinstalldirs
libdnet-1.12/trunk/configure
libdnet-1.12/trunk/configure.in
libdnet-1.12/trunk/dnet-config.in
libdnet-1.12/trunk/include/
libdnet-1.12/trunk/include/config.h.in
libdnet-1.12/trunk/include/dnet/
libdnet-1.12/trunk/include/dnet/addr.h
libdnet-1.12/trunk/include/dnet/arp.h
libdnet-1.12/trunk/include/dnet/blob.h
libdnet-1.12/trunk/include/dnet/eth.h
libdnet-1.12/trunk/include/dnet/fw.h
libdnet-1.12/trunk/include/dnet/icmp.h
libdnet-1.12/trunk/include/dnet/intf.h
libdnet-1.12/trunk/include/dnet/ip.h
libdnet-1.12/trunk/include/dnet/ip6.h
libdnet-1.12/trunk/include/dnet/Makefile.am
libdnet-1.12/trunk/include/dnet/Makefile.in
libdnet-1.12/trunk/include/dnet/os.h
libdnet-1.12/trunk/include/dnet/rand.h
libdnet-1.12/trunk/include/dnet/route.h
libdnet-1.12/trunk/include/dnet/tcp.h
libdnet-1.12/trunk/include/dnet/tun.h
libdnet-1.12/trunk/include/dnet/udp.h
libdnet-1.12/trunk/include/dnet.h
libdnet-1.12/trunk/include/err.h
libdnet-1.12/trunk/include/Makefile.am
libdnet-1.12/trunk/include/Makefile.in
libdnet-1.12/trunk/include/queue.h
libdnet-1.12/trunk/include/stamp-h.in
libdnet-1.12/trunk/INSTALL
libdnet-1.12/trunk/libdnet.spec
libdnet-1.12/trunk/LICENSE
libdnet-1.12/trunk/Makefile.am
libdnet-1.12/trunk/Makefile.am.common
libdnet-1.12/trunk/Makefile.in
libdnet-1.12/trunk/man/
libdnet-1.12/trunk/man/dnet.3
libdnet-1.12/trunk/man/Makefile.am
libdnet-1.12/trunk/man/Makefile.in
libdnet-1.12/trunk/python/
libdnet-1.12/trunk/python/dnet.c
libdnet-1.12/trunk/python/dnet.pyx
libdnet-1.12/trunk/python/Makefile.am
libdnet-1.12/trunk/python/Makefile.in
libdnet-1.12/trunk/python/pyrex.diff
libdnet-1.12/trunk/python/setup.py.in
libdnet-1.12/trunk/python/test.py
libdnet-1.12/trunk/README
libdnet-1.12/trunk/src/
libdnet-1.12/trunk/src/addr-util.c
libdnet-1.12/trunk/src/addr.c
libdnet-1.12/trunk/src/arp-bsd.c
libdnet-1.12/trunk/src/arp-ioctl.c
libdnet-1.12/trunk/src/arp-none.c
libdnet-1.12/trunk/src/arp-win32.c
libdnet-1.12/trunk/src/blob.c
libdnet-1.12/trunk/src/err.c
libdnet-1.12/trunk/src/eth-bsd.c
libdnet-1.12/trunk/src/eth-dlpi.c
libdnet-1.12/trunk/src/eth-linux.c
libdnet-1.12/trunk/src/eth-ndd.c
libdnet-1.12/trunk/src/eth-none.c
libdnet-1.12/trunk/src/eth-pfilt.c
libdnet-1.12/trunk/src/eth-snoop.c
libdnet-1.12/trunk/src/eth-win32.c
libdnet-1.12/trunk/src/fw-ipchains.c
libdnet-1.12/trunk/src/fw-ipf.c
libdnet-1.12/trunk/src/fw-ipfw.c
libdnet-1.12/trunk/src/fw-none.c
libdnet-1.12/trunk/src/fw-pf.c
libdnet-1.12/trunk/src/fw-pktfilter.c
libdnet-1.12/trunk/src/intf-win32.c
libdnet-1.12/trunk/src/intf.c
libdnet-1.12/trunk/src/ip-cooked.c
libdnet-1.12/trunk/src/ip-util.c
libdnet-1.12/trunk/src/ip-win32.c
libdnet-1.12/trunk/src/ip.c
libdnet-1.12/trunk/src/ip6.c
libdnet-1.12/trunk/src/Makefile.am
libdnet-1.12/trunk/src/Makefile.in
libdnet-1.12/trunk/src/memcmp.c
libdnet-1.12/trunk/src/rand.c
libdnet-1.12/trunk/src/route-bsd.c
libdnet-1.12/trunk/src/route-hpux.c
libdnet-1.12/trunk/src/route-linux.c
libdnet-1.12/trunk/src/route-none.c
libdnet-1.12/trunk/src/route-win32.c
libdnet-1.12/trunk/src/strlcat.c
libdnet-1.12/trunk/src/strlcpy.c
libdnet-1.12/trunk/src/strsep.c
libdnet-1.12/trunk/src/tun-bsd.c
libdnet-1.12/trunk/src/tun-linux.c
libdnet-1.12/trunk/src/tun-none.c
libdnet-1.12/trunk/src/tun-solaris.c
libdnet-1.12/trunk/test/
libdnet-1.12/trunk/test/check/
libdnet-1.12/trunk/test/check/check_addr.c
libdnet-1.12/trunk/test/check/check_arp.c
libdnet-1.12/trunk/test/check/check_blob.c
libdnet-1.12/trunk/test/check/check_eth.c
libdnet-1.12/trunk/test/check/check_fw.c
libdnet-1.12/trunk/test/check/check_intf.c
libdnet-1.12/trunk/test/check/check_ip.c
libdnet-1.12/trunk/test/check/check_rand.c
libdnet-1.12/trunk/test/check/check_route.c
libdnet-1.12/trunk/test/check/Makefile.am
libdnet-1.12/trunk/test/check/Makefile.in
libdnet-1.12/trunk/test/dnet/
libdnet-1.12/trunk/test/dnet/addr.c
libdnet-1.12/trunk/test/dnet/arp.c
libdnet-1.12/trunk/test/dnet/aton.c
libdnet-1.12/trunk/test/dnet/aton.h
libdnet-1.12/trunk/test/dnet/dnet.8
libdnet-1.12/trunk/test/dnet/dnet.c
libdnet-1.12/trunk/test/dnet/eth.c
libdnet-1.12/trunk/test/dnet/fw.c
libdnet-1.12/trunk/test/dnet/hex.c
libdnet-1.12/trunk/test/dnet/icmp.c
libdnet-1.12/trunk/test/dnet/intf.c
libdnet-1.12/trunk/test/dnet/ip.c
libdnet-1.12/trunk/test/dnet/Makefile.am
libdnet-1.12/trunk/test/dnet/Makefile.in
libdnet-1.12/trunk/test/dnet/mod.h
libdnet-1.12/trunk/test/dnet/rand.c
libdnet-1.12/trunk/test/dnet/route.c
libdnet-1.12/trunk/test/dnet/send.c
libdnet-1.12/trunk/test/dnet/tcp.c
libdnet-1.12/trunk/test/dnet/udp.c
libdnet-1.12/trunk/test/Makefile.am
libdnet-1.12/trunk/test/Makefile.in
libdnet-1.12/trunk/THANKS
libdnet-1.12/trunk/TODO
mroth@cldnids01:~$ cd libdnet-1.12/
mroth@cldnids01:~/libdnet-1.12$ sudo ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... file_magic ELF [0-9][0-9]*-bit [LM]SB (shared object|dynamic lib )
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for file... /usr/bin/file
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... no
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) no
appending configuration tag "F77" to libtool
checking for Python... checking for gethostbyname... yes
checking for socket... yes
checking for putmsg in -lstr... no
checking for open_mib in -lnm... no
checking for Check... no
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking sys/bufmod.h usability... no
checking sys/bufmod.h presence... no
checking for sys/bufmod.h... no
checking sys/dlpi.h usability... no
checking sys/dlpi.h presence... no
checking for sys/dlpi.h... no
checking sys/dlpihdr.h usability... no
checking sys/dlpihdr.h presence... no
checking for sys/dlpihdr.h... no
checking sys/dlpi_ext.h usability... no
checking sys/dlpi_ext.h presence... no
checking for sys/dlpi_ext.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/mib.h usability... no
checking sys/mib.h presence... no
checking for sys/mib.h... no
checking sys/ndd_var.h usability... no
checking sys/ndd_var.h presence... no
checking for sys/ndd_var.h... no
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking net/bpf.h usability... no
checking net/bpf.h presence... no
checking for net/bpf.h... no
checking net/if.h usability... yes
checking net/if.h presence... yes
checking for net/if.h... yes
checking net/if_var.h usability... no
checking net/if_var.h presence... no
checking for net/if_var.h... no
checking net/if_arp.h usability... yes
checking net/if_arp.h presence... yes
checking for net/if_arp.h... yes
checking net/if_dl.h usability... no
checking net/if_dl.h presence... no
checking for net/if_dl.h... no
checking net/pfilt.h usability... no
checking net/pfilt.h presence... no
checking for net/pfilt.h... no
checking net/pfvar.h usability... no
checking net/pfvar.h presence... no
checking for net/pfvar.h... no
checking net/radix.h usability... no
checking net/radix.h presence... no
checking for net/radix.h... no
checking net/raw.h usability... no
checking net/raw.h presence... no
checking for net/raw.h... no
checking net/route.h usability... yes
checking net/route.h presence... yes
checking for net/route.h... yes
checking netinet/in_var.h usability... no
checking netinet/in_var.h presence... no
checking for netinet/in_var.h... no
checking net/if_tun.h usability... no
checking net/if_tun.h presence... no
checking for net/if_tun.h... no
checking linux/if_tun.h usability... yes
checking linux/if_tun.h presence... yes
checking for linux/if_tun.h... yes
checking netinet/ip_fw.h usability... no
checking netinet/ip_fw.h presence... no
checking for netinet/ip_fw.h... no
checking linux/ip_fw.h usability... no
checking linux/ip_fw.h presence... no
checking for linux/ip_fw.h... no
checking linux/ip_fwchains.h usability... no
checking linux/ip_fwchains.h presence... no
checking for linux/ip_fwchains.h... no
checking linux/netfilter_ipv4/ipchains_core.h usability... no
checking linux/netfilter_ipv4/ipchains_core.h presence... no
checking for linux/netfilter_ipv4/ipchains_core.h... no
checking ip_fil_compat.h usability... no
checking ip_fil_compat.h presence... no
checking for ip_fil_compat.h... no
checking netinet/ip_fil_compat.h usability... no
checking netinet/ip_fil_compat.h presence... no
checking for netinet/ip_fil_compat.h... no
checking ip_compat.h usability... no
checking ip_compat.h presence... no
checking for ip_compat.h... no
checking netinet/ip_compat.h usability... no
checking netinet/ip_compat.h presence... no
checking for netinet/ip_compat.h... no
checking ip_fil.h usability... no
checking ip_fil.h presence... no
checking for ip_fil.h... no
checking netinet/ip_fil.h usability... no
checking netinet/ip_fil.h presence... no
checking for netinet/ip_fil.h... no
checking hpsecurity.h usability... no
checking hpsecurity.h presence... no
checking for hpsecurity.h... no
checking stropts.h usability... yes
checking stropts.h presence... yes
checking for stropts.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for pid_t... yes
checking for size_t... yes
checking for sockaddr_in6 struct in <netinet/in.h>... yes
checking for sa_len in sockaddr struct... no
checking for arp_dev in arpreq struct... yes
checking for rt_msghdr struct in <net/route.h>... no
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for err... yes
checking for strlcat... no
checking for strlcpy... no
checking for strsep... yes
checking for Berkeley Packet Filter... no
checking for Linux proc filesystem... yes
checking for Linux PF_PACKET sockets... yes
checking for SNMP MIB2 STREAMS... no
checking for route(7) STREAMS... no
checking for arp(7) ioctls... yes
checking for raw IP sockets ip_{len,off} host byte ordering... no
checking for cooked raw IP sockets... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating dnet-config
config.status: creating include/Makefile
config.status: creating include/dnet/Makefile
config.status: creating man/Makefile
config.status: creating src/Makefile
config.status: creating python/Makefile
config.status: creating python/setup.py
config.status: creating test/Makefile
config.status: creating test/check/Makefile
config.status: creating test/dnet/Makefile
config.status: creating include/config.h
config.status: executing depfiles commands
config.status: executing default commands

```

---

### Post by sdmike6 on 2011-08-02
I'm a dork I forgot on a fresh install on Ubuntu Server that make is not installed.

---

