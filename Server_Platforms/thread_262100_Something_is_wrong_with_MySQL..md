---
title: "Something is wrong with MySQL."
date: 2006-09-21
forum: Server Platforms
---

### Post by JoshX on 2006-09-21
When i run "./configure --with-mysql-lib-dir=/usr/local/mysql", i get:
```

josh@joshlinux:~/mangos$ ./configure --with-mysql-lib-dir=/usr/local/mysql
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
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
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static ./configure --with-mysql-lib-dir=/usr/local/mysqlflag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking for python... /usr/bin/python
./configure: line 18547: +: command not found
checking for pthread_create in -lpthread... yes
checking for compress in -lz... yes
checking for ftime  in -lcompat... no
checking for mysql_init in -lmysqlclient_r... no
checking for mysql_init in -lmysql... no
configure: error: Missing mysql

```

But I already have done this earlier:
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

And apache is on, same as MySQL ([http://localhost](http://localhost) works). Any ideas?

---

### Post by gmarton on 2006-09-21
I use php4 and these 3 lines did the trick for me:

> 
sudo apt-get install mysql-server mysql-client libmysqlclient12-dev

sudo apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert 

sudo apt-get install autoconf automake1.4 autotools-dev libapache2-mod-php4 php4 php4-common php4-curl php4-dev php4-gd php-pear php4-ldap php4-mhash php4-mysql php4-snmp php4-imap php4-mcrypt php4-pspell



Make sure Universe is enabled in your /etc/apt/sources.list
and then you can do 

> sudo apt-get install phpmyadmin 
hope this helps

---

### Post by Josh1 on 2006-09-21
Thanks, now for a silly question, how do i start apache, mysql? I was using XAMPP before.
Thanks,
Josh

---

### Post by gmarton on 2006-09-21
Apache2:
> sudo /etc/init.d/apache2 start

Usage: /etc/init.d/apache2 start|stop|restart|reload|force-reload

and mysql : 
> 
sudo /etc/init.d/mysql start

Usage: /etc/init.d/mysql start|stop|restart|reload|force-reload|status

look in /etc/init.d/ to about starting/restarting other services.

---

### Post by Josh1 on 2006-09-22
Thank you so much! That seems to have fixed the problem :D!

---

### Post by spp on 2006-09-22
Just as a quick note, anytime you are compiling something from scratch and it says it is missing something, make sure you install the -dev or -devel packages for the missing item. What it is actually looking for is the headers to compile against and the standard package *usually* does not include them.

SP

---

### Post by Josh1 on 2006-09-22
> **spp said:**
> Just as a quick note, anytime you are compiling something from scratch and it says it is missing something, make sure you install the -dev or -devel packages for the missing item. What it is actually looking for is the headers to compile against and the standard package *usually* does not include them.

SP
Ahh, thanks for the tip, ssp! I will have to remember that :D.

---

