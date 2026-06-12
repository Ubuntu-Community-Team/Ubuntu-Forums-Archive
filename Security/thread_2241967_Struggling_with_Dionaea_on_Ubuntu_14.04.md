---
title: "Struggling with Dionaea on Ubuntu 14.04"
date: 2014-08-29
forum: Security
---

### Post by z3nl4k1n on 2014-08-29
I am trying to get Dionaea up and running on a fresh Ubuntu 14.04 VM that I have created and fully updated. I have followed all of the instructions on this site: [http://edgis-security.org/honeypot/dionaea-02-setting-up-a-dionaea-honeypot/]("http://edgis-security.org/honeypot/dionaea-02-setting-up-a-dionaea-honeypot/#comment-4980"). Below is the output I receive when running the final command to check if everything was installed correctly. From what I can tell it seems that the issue resides in libemu but I can't seem to pinpoint what I need to do as I have downloaded libemu-0.2.0 thinking maybe I needed a newer version but that still doesn't seem to allow the check script to pass. 


```
/opt/dionaea$ sudo ./configure --with-lcfg-include=/opt/dionaea/include/ --with-lcfg-lib=/opt/dionaea/lib/ --with-python=/opt/dionaea/bin/python3.4 --with-cython-dir=/opt/dionaea/bin --with-udns-include=/opt/dionaea/include/ --with-udns-lib=/opt/dionaea/lib/ --with-emu-include=/opt/dionaea/include/ --with-emu-lib=/opt/dionaea/lib/ --with-gc-include=/usr/include/gc --with-ev-include=/opt/dionaea/include --with-ev-lib=/opt/dionaea/lib --with-nl-include=/opt/dionaea/include --with-nl-lib=/opt/dionaea/lib/ --with-curl-config=/usr/bin/ --with-pcap-include=/opt/dionaea/include --with-pcap-lib=/opt/dionaea/lib/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking for an ANSI C-conforming const... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking whether make sets $(MAKE)... (cached) yes
checking how to print strings... printf
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking for dlfcn.h... yes
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
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking netpacket/packet.h usability... yes
checking netpacket/packet.h presence... yes
checking for netpacket/packet.h... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking linux/sockios.h usability... yes
checking linux/sockios.h presence... yes
checking for linux/sockios.h... yes
checking for inline... inline
checking for uid_t in sys/types.h... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for size_t... yes
checking return type of signal handlers... void
checking for error_at_line... yes
checking return type of signal handlers... (cached) void
checking for strndup... yes
checking for inet_ntoa... yes
checking for memmove... yes
checking for memset... yes
checking for strdup... yes
checking for strerror... yes
checking for bind... yes
checking if bind("::ffff:0.0.0.0") works... yes
checking ev.h usability... yes
checking ev.h presence... yes
checking for ev.h... yes
checking for ev_run in -lev... yes
checking emu/emu.h usability... no
checking emu/emu.h presence... no
checking for emu/emu.h... no
checking cspm/cspm.h usability... no
checking cspm/cspm.h presence... no
checking for cspm/cspm.h... no
checking udns.h usability... yes
checking udns.h presence... yes
checking for udns.h... yes
checking for dns_submit_p in -ludns... yes
checking gc.h usability... no
checking gc.h presence... no
checking for gc.h... no
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking for SSL_connect in -lssl... yes
checking pcap/sll.h usability... yes
checking pcap/sll.h presence... yes
checking for pcap/sll.h... yes
checking for pcap_open_live in -lpcap... yes
checking libnetfilter_queue/libnetfilter_queue.h usability... no
checking libnetfilter_queue/libnetfilter_queue.h presence... no
checking for libnetfilter_queue/libnetfilter_queue.h... no
checking xmatch.h usability... no
checking xmatch.h presence... no
checking for xmatch.h... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for glib... yes
checking for gthread... yes
checking for gmodule... yes
checking for --enable-python... no
checking for --with-python... /opt/dionaea/bin/python3.4
checking for python3.2... /opt/dionaea/bin/python3.4
checking whether /opt/dionaea/bin/python3.4 version >= 3.2 ... yes
configure: PYTHON_CSPEC=-fPIC -I/opt/dionaea/include/python3.4m
configure: PYTHON_LSPEC= -Xlinker -export-dynamic -lm -lpthread -ldl  -lutil -lpython3.4m
checking for cython... /opt/dionaea/bin/cython
checking lcfg/lcfg.h usability... yes
checking lcfg/lcfg.h presence... yes
checking for lcfg/lcfg.h... yes
checking for lcfg_new in -llcfg... yes
checking netlink/netlink.h usability... no
checking netlink/netlink.h presence... no
checking for netlink/netlink.h... no
checking for curl-config... /usr/bin//curl-config
checking for loudmouth... no
checking for loudmouth... no
checking whether you are looking for 'performance'... no
checking whether debug code generation should be enabled... yes
checking whether you want Werror... yes
checking DEPENDENCY emu... configure: WARNING: no
checking DEPENDENCY ev... yes
checking DEPENDENCY curl... yes
checking DEPENDENCY cython... yes
checking DEPENDENCY python... yes
checking DEPENDENCY glib... yes
checking DEPENDENCY udns... yes
checking DEPENDENCY ssl... yes
checking if all required dependencies are installed properly... configure: error: no - better read the documentation
```

---

### Post by ptroxell000 on 2014-09-19
I used the libemu-dev package so I didn't have to compile it. When doing the configure for dionaea leave off the --with-emu-include and --with-emu-lib options as the configure script will find them just fine. I also had to change the nl options since he was using the package instead of source code. Here is my configure line:

./configure --enable-gc \
      --with-lcfg-include=/opt/dionaea/include/ \
      --with-lcfg-lib=/opt/dionaea/lib/ \
      --with-python=/opt/dionaea/bin/python3.4 \
      --with-cython-dir=/opt/dionaea/bin \
      --with-gc-include=/usr/include/gc \
      --with-ev-include=/opt/dionaea/include \
      --with-ev-lib=/opt/dionaea/lib \
      --with-curl-config=/usr/bin/ \
      --with-nl-include=/usr/include/libnl3 \
      --with-pcap-include=/opt/dionaea/include \
      --with-pcap-lib=/opt/dionaea/lib/

This gave me a good configure but now make fails due to the -Werror option to gcc. Seems they are using some deprecated calls...

You can edit src/Makefile and search for and remove -Werror from the CFLAGS setting. This get it past the compile stage but now fails on linking with an undefined reference to to symbol 'X509_gmtime_adj@@OPENSSL_1.0.0'. I'm still working on that one...

Pete

---

### Post by Frogs Hair on 2014-09-20
The link includes instructions for 12.04 and some libs have probably changed ,so finding out if this instruction is still valid for 14.04 would be a good idea before getting too frustrated trying to install the program.There have also been point releases for 12.04 since the tutorial was posted.

[http://edgis-security.org/honeypot/dionaea-02-setting-up-a-dionaea-honeypot/#comment-4980](http://edgis-security.org/honeypot/dionaea-02-setting-up-a-dionaea-honeypot/#comment-4980)

---

