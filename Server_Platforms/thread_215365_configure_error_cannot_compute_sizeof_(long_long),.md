---
title: "configure: error: cannot compute sizeof (long long), 77"
date: 2006-07-13
forum: Server Platforms
---

### Post by randomnote1 on 2006-07-13
I'm trying to install Bro, a network intrusion system, and I keep running into this error.

```
checking size of long long... configure: error: cannot compute sizeof (long long), 77
```

I downloaded it from [http://bro-ids.org/download.html]("http://bro-ids.org/download.html") .  Here's the output from when I type 
```
sudo ./configure
```

```
daniel@daniel-itt:~/downloads/bro-0.9a11$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets ${MAKE}... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking for flex... flex
checking for flex... (cached) flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for gzip... gzip
checking for OPENSSL_add_all_algorithms_conf in -lcrypto... no
checking for perl5... no
checking for perl... /usr/bin/perl
checking for chown... /bin/chown
checking Linux kernel version... 2
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking return type of signal handlers... void
checking for sigset... yes
checking for int32_t using gcc... yes
checking for u_int32_t using gcc... yes
checking for u_int16_t using gcc... yes
checking for u_int8_t using gcc... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for memory.h... (cached) yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking socket.h usability... no
checking socket.h presence... no
checking for socket.h... no
checking for net/ethernet.h... yes
checking for netinet/ether.h... yes
checking for netinet/if_ether.h... yes
checking for netinet/ip6.h... yes
checking for socklen_t... yes
checking if syslog returns int... no
checking if we should declare socket and friends... no
checking for working memcmp... yes
checking for strftime... yes
checking for strerror... yes
checking for strsep... yes
checking for mallinfo... yes
checking for library containing inet_aton... none required
checking for ns_initparse in -lresolv... no
checking for ns_initparse in resolver... yes
checking for tgetnum in -ltermcap... no
checking for termcap in /usr/lib/termcap/... no
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
checking whether byte ordering is bigendian... no
checking for ns_msg... yes
checking for res_mkquery... no
checking for res_mkquery in -lresolv... no
checking for res_mkquery/res_nmkquery as last chance... yes
checking for union semun... no
checking for struct sembuf... yes
checking for struct sockaddr_in.sin_len... no
checking for long long... yes
checking size of long long... configure: error: cannot compute sizeof (long long), 77

```

Any help anybody can give me would be greatly appreciated.  Thanks!

---

### Post by Sreejithb4u on 2007-09-21
I also get the same error when installing gcc4.2

.
.
.
checking for long long... yes
checking size of long long... configure: error: cannot determine a size for long long
make: *** [configure-bfd] Error 1


how do i solve it?????:lolflag:

---

### Post by koenn on 2007-09-21
it's probably a bug - the script seems to check the size of a variable ('long'), but fails to do so. It can be either a bug in the configure/make files, or in the source of the program itself
That, or your system does not meet all conditions for a succesfull compile of this program. 
I suggest you try to find out more from the docs, or report a bug

---

### Post by Sreejithb4u on 2007-09-24
[COLOR="Red"][COLOR="Red"][COLOR="Red"][COLOR="Red"]checking for sys/types.h... no
checking for sys/stat.h... no
checking for stdlib.h... no
checking for string.h... yes
checking for memory.h... no
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for long long... yes
checking size of long long... configure: error: cannot compute sizeof (long long), 77
See `config.log' for more details.
make[1]: *** [configure-bfd] Error 1
make[1]: Leaving directory `/home/Sreejith/binutils-2.17.50.0.6'
make: *** [all] Error 2
[/COLOR][/COLOR][/COLOR][/COLOR]

Where is the bug likely to be.... 


How do i fix it....

What invokes these bugs.....?


Please explain....:confused:

---

### Post by koenn on 2007-09-24
> **koenn said:**
>  It can be either a bug in the configure/make files, or in the source of the program itself
That, or your system does not meet all conditions for a succesfull compile of this program. 
did you install the build-essential package ? It's required to do his sort of compiling. 

[http://en.wikipedia.org/wiki/Software_bug](http://en.wikipedia.org/wiki/Software_bug)

if it's a bug, then unless you understand programming well enough to modify the configure script or the source code of the program, there's little you can do.

also: have a look at  `config.log' for more details. config.log will be in the directory where you ran ./configure

---

### Post by Sreejithb4u on 2007-10-01
The problem has been solved only when i reinstalled linux...


So anybody who whats it to be solved immediately please resintall the Linux once again 

I thin the cause is due to gcc file getting corrupted

:guitar:

---

