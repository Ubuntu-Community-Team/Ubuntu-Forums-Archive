---
title: "installing pvpgn"
date: 2009-09-11
forum: Server Platforms
---

### Post by I WILL DO IT on 2009-09-11
so am trying to get pvpgn installed on my comp, can some one help.
I've looked at the many of guides and yet and still puzzled.

---

### Post by hikaricore on 2009-09-11
You may want to describe what you're trying to do a little better.. I have no idea what pvpgn is and others might not either.

---

### Post by I WILL DO IT on 2009-09-11
this is pvpgn 

[http://pvpgn.berlios.de/](http://pvpgn.berlios.de/)

---

### Post by Perfect Storm on 2009-09-11
Hmm...


```
cd ~/Desktop
wget http://download.berlios.de/pvpgn/pvpgn-1.8.5.tar.gz
tar zxfv pvpgn-1.8.5.tar.gz
cd pvpgn-1.8.5/src
./configure --help
```

Then flag ./configure with the stuff you need it with.

You definitely need to install build-essential at first.
```
sudo apt-get install build-essential
```

When you run ./configure with the flags you want to enable, please post the output, so we can see which dependency libs you need.


Here's the flags;
```
Usage: configure [options] [host]                           
Options: [defaults in brackets after descriptions]          
Configuration:                                              
  --cache-file=FILE       cache test results in FILE        
  --help                  print this message                
  --no-create             do not create output files        
  --quiet, --silent       do not print `checking...' messages
  --version               print the version of autoconf that created configure                                                          
Directory and file names:                                           
  --prefix=PREFIX         install architecture-independent files in PREFIX                                                              
                          [/usr/local]                              
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX                                                               
                          [same as prefix]                          
  --bindir=DIR            user executables in DIR [EPREFIX/bin]     
  --sbindir=DIR           system admin executables in DIR [EPREFIX/sbin]                                                                
  --libexecdir=DIR        program executables in DIR [EPREFIX/libexec]                                                                  
  --datadir=DIR           read-only architecture-independent data in DIR                                                                
                          [PREFIX/share]                            
  --sysconfdir=DIR        read-only single-machine data in DIR [PREFIX/etc]                                                             
  --sharedstatedir=DIR    modifiable architecture-independent data in DIR                                                               
                          [PREFIX/com]                              
  --localstatedir=DIR     modifiable single-machine data in DIR [PREFIX/var]                                                            
  --libdir=DIR            object code libraries in DIR [EPREFIX/lib]
  --includedir=DIR        C header files in DIR [PREFIX/include]    
  --oldincludedir=DIR     C header files for non-gcc in DIR [/usr/include]                                                              
  --infodir=DIR           info documentation in DIR [PREFIX/info]   
  --mandir=DIR            man documentation in DIR [PREFIX/man]     
  --srcdir=DIR            find the sources in DIR [configure dir or ..]                                                                 
  --program-prefix=PREFIX prepend PREFIX to installed program names 
  --program-suffix=SUFFIX append SUFFIX to installed program names  
  --program-transform-name=PROGRAM                                  
                          run sed PROGRAM on installed program names
Host type:                                                          
  --build=BUILD           configure for building on BUILD [BUILD=HOST]                                                                  
  --host=HOST             configure for HOST [guessed]              
  --target=TARGET         configure for TARGET [TARGET=HOST]        
Features and packages:                                              
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)                                                          
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]                 
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]                     
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)                                                                
  --x-includes=DIR        X include files are in DIR                
  --x-libraries=DIR       X library files are in DIR                
--enable and --with options recognized:                             
  --with-warn             enable compiler warnings                  
  --with-ansi             use ANSI C mode                           
  --with-includes=DIR     search include DIR for header files       
  --with-libraries=DIR    search library DIR for libraries          
  --with-efence           link with Electric Fence to find memory problems                                                              
  --with-mysql            include MySQL user accounts support       
  --with-pgsql            include PostgreSQL user accounts support  
  --with-mssql            include MSSQL user accounts support (requires FreeTDS includes/libs)                                          
  --with-sqlite3          include SQLite3 user accounts support
  --with-odbc             include ODBC user accounts support
  --enable-poll           Enable poll() instead of select().  Normally poll
                          is preferred over select, but configure knows poll
                          is broken on some platforms.  If you think you are
                          smarter than the configure script, you may enable
                          poll with this option.
  --disable-poll          Disable the use of poll().
  --enable-bnetd          Enable building of bnetd server (default)
  --disable-bnetd         Disable building of bnetd server
  --enable-d2cs           Enable building of d2cs server (default)
  --disable-d2cs          Disable building of d2cs server
  --enable-d2dbs          Enable building of d2dbs server (default)
  --disable-d2dbs         Disable building of d2dbs server
```

---

### Post by I WILL DO IT on 2009-09-12
**[SIZE="4"]mmmm is this what you mean??[/SIZE]**



```
cool@cool-desktop:~/Desktop$ cd pvpgn-1.8.5/src
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ ./configure --help
Usage: configure [options] [host]
Options: [defaults in brackets after descriptions]
Configuration:
  --cache-file=FILE       cache test results in FILE
  --help                  print this message
  --no-create             do not create output files
  --quiet, --silent       do not print `checking...' messages
  --version               print the version of autoconf that created configure
Directory and file names:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [same as prefix]
  --bindir=DIR            user executables in DIR [EPREFIX/bin]
  --sbindir=DIR           system admin executables in DIR [EPREFIX/sbin]
  --libexecdir=DIR        program executables in DIR [EPREFIX/libexec]
  --datadir=DIR           read-only architecture-independent data in DIR
                          [PREFIX/share]
  --sysconfdir=DIR        read-only single-machine data in DIR [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data in DIR
                          [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data in DIR [PREFIX/var]
  --libdir=DIR            object code libraries in DIR [EPREFIX/lib]
  --includedir=DIR        C header files in DIR [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc in DIR [/usr/include]
  --infodir=DIR           info documentation in DIR [PREFIX/info]
  --mandir=DIR            man documentation in DIR [PREFIX/man]
  --srcdir=DIR            find the sources in DIR [configure dir or ..]
  --program-prefix=PREFIX prepend PREFIX to installed program names
  --program-suffix=SUFFIX append SUFFIX to installed program names
  --program-transform-name=PROGRAM
                          run sed PROGRAM on installed program names
Host type:
  --build=BUILD           configure for building on BUILD [BUILD=HOST]
  --host=HOST             configure for HOST [guessed]
  --target=TARGET         configure for TARGET [TARGET=HOST]
Features and packages:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --x-includes=DIR        X include files are in DIR
  --x-libraries=DIR       X library files are in DIR
--enable and --with options recognized:
  --with-warn             enable compiler warnings
  --with-ansi             use ANSI C mode
  --with-includes=DIR     search include DIR for header files
  --with-libraries=DIR    search library DIR for libraries
  --with-efence           link with Electric Fence to find memory problems
  --with-mysql            include MySQL user accounts support
  --with-pgsql            include PostgreSQL user accounts support
  --with-mssql            include MSSQL user accounts support (requires FreeTDS includes/libs)
  --with-sqlite3          include SQLite3 user accounts support 
  --with-odbc             include ODBC user accounts support 
  --enable-poll           Enable poll() instead of select().  Normally poll
                          is preferred over select, but configure knows poll
                          is broken on some platforms.  If you think you are
                          smarter than the configure script, you may enable
                          poll with this option.
  --disable-poll          Disable the use of poll().
  --enable-bnetd          Enable building of bnetd server (default)
  --disable-bnetd         Disable building of bnetd server
  --enable-d2cs           Enable building of d2cs server (default)
  --disable-d2cs          Disable building of d2cs server
  --enable-d2dbs          Enable building of d2dbs server (default)
  --disable-d2dbs         Disable building of d2dbs server
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ sudo apt-get install build-essential
[sudo] password for cool: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up rocksndiamonds (3.2.6.0+dfsg-6) ...
Update menu
sh: update-menus: not found
--2009-09-12 01:08:08--  [http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.6.0.tar.gz](http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.6.0.tar.gz)
Resolving [www.artsoft.org](www.artsoft.org)... 195.71.106.28
Connecting to [www.artsoft.org|195.71.106.28|:80](www.artsoft.org|195.71.106.28|:80)... failed: Connection refused.
wget -c -P /usr/share/games/rocksndiamonds/downloads [http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.6.0.tar.gz](http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.6.0.tar.gz)
Error code: 256
Can not download [http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.6.0.tar.gz](http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.6.0.tar.gz)
dpkg: error processing rocksndiamonds (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 rocksndiamonds
E: Sub-process /usr/bin/dpkg returned an error code (1)
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking for POSIXized ISC... no
checking for minix/config.h... no
checking whether gcc needs -traditional... no
checking for gcc option to accept ANSI C... none needed
checking for working const... yes
checking for inline... inline
checking for pow in -lm... yes
checking for compress in -lz... no
checking for gethostbyname in -lnsl... yes
checking for socket in -lsocket... no
checking for inet_aton in -lresolv... yes
checking for __inet_aton in -lbind... no
checking for _libwsock32_a_iname in -lwsock32... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether stat file-mode macros are broken... no
checking for fcntl.h... yes
checking for sys/time.h... yes
checking for time.h... yes
checking for sys/select.h... yes
checking for string.h... yes
checking for strings.h... yes
checking for unistd.h... yes
checking for stdarg.h... yes
checking for varargs.h... no
checking for malloc.h... yes
checking for sys/utsname.h... yes
checking for sys/timeb.h... yes
checking for sys/socket.h... yes
checking for sys/param.h... yes
checking for netinet/in.h... yes
checking for arpa/inet.h... yes
checking for netdb.h... yes
checking for termios.h... yes
checking for stddef.h... yes
checking for memory.h... yes
checking for sys/types.h... yes
checking for sys/wait.h... yes
checking for sys/ioctl.h... yes
checking for stdint.h... yes
checking for sys/file.h... yes
checking for limits.h... yes
checking for poll.h... yes
checking for sys/poll.h... yes
checking for stropts.h... yes
checking for sys/stropts.h... yes
checking for sys/stat.h... yes
checking for pwd.h... yes
checking for grp.h... yes
checking for dir.h... no
checking for direct.h... no
checking for sys/mman.h... yes
checking for sys/event.h... no
checking for sys/epoll.h... yes
checking for sys/resource.h... yes
checking for assert.h... yes
checking for sqlite3.h... no
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking return type of signal handlers... void
checking for off_t... yes
checking for size_t... yes
checking size of unsigned char... 1
checking size of unsigned short... 2
checking size of unsigned int... 4
checking size of unsigned long... 4
checking size of unsigned long long... 8
checking size of signed char... 1
checking size of signed short... 2
checking size of signed int... 4
checking size of signed long... 4
checking size of signed long long... 8
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for strftime... yes
checking for vprintf... yes
checking whether closedir returns void... no
checking for mkdir... yes
checking for _mkdir... no
checking whether mkdir takes one argument... no
checking for gethostname... yes
checking for gettimeofday... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strtoul... yes
checking for strerror... yes
checking for inet_aton... yes
checking for inet_ntoa... yes
checking for uname... yes
checking for recv... yes
checking for send... yes
checking for recvfrom... yes
checking for sendto... yes
checking for uname... (cached) yes
checking for fork... yes
checking for getpid... yes
checking for sigaction... yes
checking for sigprocmask... yes
checking for sigaddset... yes
checking for setpgid... yes
checking for setpgrp... yes
checking for ftime... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for stricmp... no
checking for strnicmp... no
checking for chdir... yes
checking for difftime... yes
checking for strchr... yes
checking for strrchr... yes
checking for index... yes
checking for rindex... yes
checking for memcpy... yes
checking for memset... yes
checking for memmove... yes
checking for bcopy... yes
checking for wait... yes
checking for waitpid... yes
checking for pipe... yes
checking for getenv... yes
checking for ioctl... yes
checking for setsid... yes
checking for mktime... yes
checking for poll... yes
checking for gethostbyname... yes
checking for getservbyname... yes
checking for getlogin... yes
checking for pow... yes
checking for getpwnam... yes
checking for getgrnam... yes
checking for getuid... yes
checking for getgid... yes
checking for setuid... yes
checking for setgid... yes
checking for mkdir... (cached) yes
checking for _mkdir... (cached) no
checking for strsep... yes
checking for getopt... yes
checking for kqueue... no
checking for setitimer... yes
checking for epoll_create... yes
checking for getrlimit... yes
checking for vsnprintf... yes
checking for _vsnprintf... no
checking for snprintf... yes
checking for _snprintf... no
checking whether setpgrp takes no argument... yes
updating cache ./config.cache
creating ./config.status
creating Makefile
creating config.h
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$
```

---

### Post by Perfect Storm on 2009-09-12
```
sh: update-menus: not found
--2009-09-12 01:08:08--  http://www.artsoft.org/RELEASES/unix...3.2.6.0.tar.gz
Resolving www.artsoft.org... 195.71.106.28
Connecting to www.artsoft.org|195.71.106.28|:80... failed: Connection refused.
wget -c -P /usr/share/games/rocksndiamonds/downloads http://www.artsoft.org/RELEASES/unix...3.2.6.0.tar.gz
Error code: 256
Can not download http://www.artsoft.org/RELEASES/unix...3.2.6.0.tar.gz
dpkg: error processing rocksndiamonds (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 rocksndiamonds
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is unrelated. It seems you have installed or setup something with artsoft.org in your repository which aren't working. The game rocksndiamonds. If you don't use it, you can just remove artsoft from your repository.


```
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking for POSIXized ISC... no
checking for minix/config.h... no
checking whether gcc needs -traditional... no
checking for gcc option to accept ANSI C... none needed
checking for working const... yes
checking for inline... inline
checking for pow in -lm... yes
checking for compress in -lz... no
checking for gethostbyname in -lnsl... yes
checking for socket in -lsocket... no
checking for inet_aton in -lresolv... yes
checking for __inet_aton in -lbind... no
checking for _libwsock32_a_iname in -lwsock32... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether stat file-mode macros are broken... no
checking for fcntl.h... yes
checking for sys/time.h... yes
checking for time.h... yes
checking for sys/select.h... yes
checking for string.h... yes
checking for strings.h... yes
checking for unistd.h... yes
checking for stdarg.h... yes
checking for varargs.h... no
checking for malloc.h... yes
checking for sys/utsname.h... yes
checking for sys/timeb.h... yes
checking for sys/socket.h... yes
checking for sys/param.h... yes
checking for netinet/in.h... yes
checking for arpa/inet.h... yes
checking for netdb.h... yes
checking for termios.h... yes
checking for stddef.h... yes
checking for memory.h... yes
checking for sys/types.h... yes
checking for sys/wait.h... yes
checking for sys/ioctl.h... yes
checking for stdint.h... yes
checking for sys/file.h... yes
checking for limits.h... yes
checking for poll.h... yes
checking for sys/poll.h... yes
checking for stropts.h... yes
checking for sys/stropts.h... yes
checking for sys/stat.h... yes
checking for pwd.h... yes
checking for grp.h... yes
checking for dir.h... no
checking for direct.h... no
checking for sys/mman.h... yes
checking for sys/event.h... no
checking for sys/epoll.h... yes
checking for sys/resource.h... yes
checking for assert.h... yes
checking for sqlite3.h... no
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking return type of signal handlers... void
checking for off_t... yes
checking for size_t... yes
checking size of unsigned char... 1
checking size of unsigned short... 2
checking size of unsigned int... 4
checking size of unsigned long... 4
checking size of unsigned long long... 8
checking size of signed char... 1
checking size of signed short... 2
checking size of signed int... 4
checking size of signed long... 4
checking size of signed long long... 8
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for strftime... yes
checking for vprintf... yes
checking whether closedir returns void... no
checking for mkdir... yes
checking for _mkdir... no
checking whether mkdir takes one argument... no
checking for gethostname... yes
checking for gettimeofday... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strtoul... yes
checking for strerror... yes
checking for inet_aton... yes
checking for inet_ntoa... yes
checking for uname... yes
checking for recv... yes
checking for send... yes
checking for recvfrom... yes
checking for sendto... yes
checking for uname... (cached) yes
checking for fork... yes
checking for getpid... yes
checking for sigaction... yes
checking for sigprocmask... yes
checking for sigaddset... yes
checking for setpgid... yes
checking for setpgrp... yes
checking for ftime... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for stricmp... no
checking for strnicmp... no
checking for chdir... yes
checking for difftime... yes
checking for strchr... yes
checking for strrchr... yes
checking for index... yes
checking for rindex... yes
checking for memcpy... yes
checking for memset... yes
checking for memmove... yes
checking for bcopy... yes
checking for wait... yes
checking for waitpid... yes
checking for pipe... yes
checking for getenv... yes
checking for ioctl... yes
checking for setsid... yes
checking for mktime... yes
checking for poll... yes
checking for gethostbyname... yes
checking for getservbyname... yes
checking for getlogin... yes
checking for pow... yes
checking for getpwnam... yes
checking for getgrnam... yes
checking for getuid... yes
checking for getgid... yes
checking for setuid... yes
checking for setgid... yes
checking for mkdir... (cached) yes
checking for _mkdir... (cached) no
checking for strsep... yes
checking for getopt... yes
checking for kqueue... no
checking for setitimer... yes
checking for epoll_create... yes
checking for getrlimit... yes
checking for vsnprintf... yes
checking for _vsnprintf... no
checking for snprintf... yes
checking for _snprintf... no
checking whether setpgrp takes no argument... yes
updating cache ./config.cache
creating ./config.status
creating Makefile
creating config.h
```

Seems good enough, I guess you don't want to flag your configuration?

Next;
```
make
sudo make install
```

---

### Post by I WILL DO IT on 2009-09-12
Whats next after this: 



cool@cool-desktop:~$ cd pvpgn-1.8.5/src
cool@cool-desktop:~/pvpgn-1.8.5/src$ make

Using compile command: gcc -g -O2   -DHAVE_CONFIG_H   -DBNETD_DEFAULT_CONF_FILE="/usr/local/etc/bnetd.conf" -DD2CS_DEFAULT_CONF_FILE="/usr/local/etc/d2cs.conf" -DD2DBS_DEFAULT_CONF_FILE="/usr/local/etc/d2dbs.conf" -I.   -fno-strict-aliasing -c

Linking ../sbin/bnetd
Linking ../sbin/bntrackd
Linking ../sbin/d2cs
Linking ../sbin/d2dbs
Linking ../bin/bnchat
Linking ../bin/bnpass
Linking ../bin/bnftp
Linking ../bin/bnbot
Linking ../bin/bnstat
Linking ../bin/bnilist
Linking ../bin/bni2tga
Linking ../bin/bniextract
Linking ../bin/bnibuild
Linking ../bin/tgainfo
Linking ../bin/bncdb
cool@cool-desktop:~/pvpgn-1.8.5/src$ makeinstall
bash: makeinstall: command not found
cool@cool-desktop:~/pvpgn-1.8.5/src$ sudo make install
[sudo] password for cool: 

Using compile command: gcc -g -O2   -DHAVE_CONFIG_H   -DBNETD_DEFAULT_CONF_FILE="/usr/local/etc/bnetd.conf" -DD2CS_DEFAULT_CONF_FILE="/usr/local/etc/d2cs.conf" -DD2DBS_DEFAULT_CONF_FILE="/usr/local/etc/d2dbs.conf" -I.   -fno-strict-aliasing -c

Linking ../sbin/bnetd
Linking ../sbin/bntrackd
Linking ../sbin/d2cs
Linking ../sbin/d2dbs
/usr/bin/install -c -d -m 755 //usr/local/sbin
  /usr/bin/install -c ./../sbin/bnetd //usr/local/sbin
  /usr/bin/install -c ./../sbin/bntrackd //usr/local/sbin
  /usr/bin/install -c ./../sbin/d2cs //usr/local/sbin
  /usr/bin/install -c ./../sbin/d2dbs //usr/local/sbin
Linking ../bin/bnchat
Linking ../bin/bnpass
Linking ../bin/bnftp
Linking ../bin/bnbot
Linking ../bin/bnstat
Linking ../bin/bnilist
Linking ../bin/bni2tga
Linking ../bin/bniextract
Linking ../bin/bnibuild
Linking ../bin/tgainfo
Linking ../bin/bncdb
/usr/bin/install -c -d -m 755 //usr/local/bin
  /usr/bin/install -c ./../bin/bnchat //usr/local/bin
  /usr/bin/install -c ./../bin/bnpass //usr/local/bin
  /usr/bin/install -c ./../bin/bnftp //usr/local/bin
  /usr/bin/install -c ./../bin/bnbot //usr/local/bin
  /usr/bin/install -c ./../bin/bnstat //usr/local/bin
  /usr/bin/install -c ./../bin/bnilist //usr/local/bin
  /usr/bin/install -c ./../bin/bni2tga //usr/local/bin
  /usr/bin/install -c ./../bin/bniextract //usr/local/bin
  /usr/bin/install -c ./../bin/bnibuild //usr/local/bin
  /usr/bin/install -c ./../bin/tgainfo //usr/local/bin
  /usr/bin/install -c ./../bin/bncdb //usr/local/bin
/usr/bin/install -c -d -m 755 //usr/local/man //usr/local/man/man1 //usr/local/man/man5
  /usr/bin/install -c -m 644 ./../man/bnetd.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bntrackd.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnchat.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnpass.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnbot.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnftp.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnstat.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnetd.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bni2tga.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnibuild.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bniextract.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnilist.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/tgainfo.1 //usr/local/man/man1
  /usr/bin/install -c -m 644 ./../man/bnetd.conf.5 //usr/local/man/man5
  /usr/bin/install -c -m 644 ./../man/bntext.5 //usr/local/man/man5
/usr/bin/install -c -d -m 755 //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnetd.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/ad.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/channel.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/realm.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/autoupdate.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnetd_default_user.plain //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnetd_default_user.cdb //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/versioncheck.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnmotd.txt //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnissue.txt //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnmaps.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnxplevel.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnxpcalc.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/news.txt //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/command_groups.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnban.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnhelp.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/bnalias.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/anongame_infos.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/tournament.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/topics.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/sql_DB_layout.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/sql_DB_layout2.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/address_translation.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/supportfile.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/d2cs.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/d2server.ini //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/address_translation.conf //usr/local/etc
  /usr/bin/install -c -m 644 ./../conf/d2dbs.conf //usr/local/etc
/usr/bin/install -c -d -m 755 //usr/local/var //usr/local/var/files //usr/local/var/users //usr/local/var/userscdb //usr/local/var/bnmail //usr/local/var/reports \
	//usr/local/var/chanlogs //usr/local/var/charinfo //usr/local/var/charsave //usr/local/var/bak/charsave \
	//usr/local/var/bak/charinfo //usr/local/var/ladders //usr/local/var/status \
	//usr/local/var/clans //usr/local/var/teams
  /usr/bin/install -c -m 644 ./../files/ad000001.smk //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/ad000001.mng //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/ad000004.mng //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/tos.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/newbie.save //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/termsofservice-default.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/termsofservice-enUS.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/chathelp-war3-default.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/chathelp-war3-enUS.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/chathelp-war3-frFR.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/chathelp-war3-zhCN.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/chathelp-war3-ruRU.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/newaccount-default.txt //usr/local/var/files
  /usr/bin/install -c -m 644 ./../files/newaccount-enUS.txt //usr/local/var/files
chmod u+x ./../scripts/tos.sh
./../scripts/tos.sh //usr/local/var/files
Generating Term Of Service for language "RUS"
Generating Term Of Service for language "POL"
Generating Term Of Service for language "CHI"
Generating Term Of Service for language "SIN"
Generating Term Of Service for language "HAN"
Generating Term Of Service for language "KOR"
Generating Term Of Service for language "JPN"
Generating Term Of Service for language "ITA"
Generating Term Of Service for language "BRA"
Generating Term Of Service for language "POR"
Generating Term Of Service for language "FRA"
Generating Term Of Service for language "DEU"
Generating Term Of Service for language "ESP"
Generating Term Of Service for language "USA"
Generating Term Of Service for language "ENU"
cool@cool-desktop:~/pvpgn-1.8.5/src$

---

### Post by Perfect Storm on 2009-09-12
Now it's done and installed. You can now run the application(s).

You should now have all the options for your server available, enjoy ^_^

---

### Post by I WILL DO IT on 2009-09-12
am super dum when it comes to Linux....

how do i run it?

---

### Post by Perfect Storm on 2009-09-12
> Linking ../bin/bnchat
Linking ../bin/bnpass
Linking ../bin/bnftp
Linking ../bin/bnbot
Linking ../bin/bnstat
Linking ../bin/bnilist
Linking ../bin/bni2tga
Linking ../bin/bniextract
Linking ../bin/bnibuild
Linking ../bin/tgainfo
Linking ../bin/bncdb

Here you can see which command you can use in the terminal. Usually they are in the /bin folders of your system.

eg.
Linking ../bin/bnstat

you can now type **bnstat** in the terminal (note that linux is case sensitive).
Usually it's not enough just the command with a commandline tool, so you can use **man** and/or the **--help** flag.

eg.
**man bnstat**   (press [q] to quit the manual pages)
**bnstat --help**

---

### Post by I WILL DO IT on 2009-09-12
dud you are too smart.

lm try this, i will tell you what happens

---

### Post by I WILL DO IT on 2009-09-12
now i got this error 


bnstat: could not connect to server "localhost" port 6112 (psock_connect: Connection refused)
bnstat: fatal error during handshake

---

### Post by Perfect Storm on 2009-09-12
I'll move this to the server forum as it might be people with more server expertise than me.
It may be that some ports need to be opened.

---

### Post by I WILL DO IT on 2009-09-12
ok, thx 4 all your help


i have a 2wire568: check this box	

Allow all applications (DMZplus mode) –  Set the selected computer in DMZplus mode. All inbound traffic, except traffic which has been specifically assigned to another computer using the “Allow individual applications” feature, will automatically be directed to this computer. The DMZplus-enabled computer is less secure because all unassigned firewall ports are opened for that computer.

Current DMZplus computer: cool-desktop
Note: Once DMZplus mode is selected and you click DONE, the system will issue a new IP address to the selected computer. The computer must be set to DHCP mode to receive the new IP address from the system, and you must reboot the computer. If you are changing DMZplus mode from one computer to another computer, you must reboot both computers.





And i still can't get team speak-server nore pvpgn
    
        this is the error msg:



         (Teamspeak-server)
cool@cool-desktop:~$ teamspeak-server
Exception EFCreateError in module teamspeak-server.real at 0806F095.
Cannot create file "/usr/lib/teamspeak-server/server.ini". Permission denied.
cool@cool-desktop:~$ sudo teamspeak-server
Error, Either an old instance of teamspeak is still running, or
       an other application is using the tcpquery port!
Error, Server was not started!
cool@cool-desktop:~$ sudo teamspeak-server
Error, Either an old instance of teamspeak is still running, or
       an other application is using the tcpquery port!
Error, Server was not started!
cool@cool-desktop:~$ 






          (pvpgn)
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ bnstat
bnstat: could not connect to server "localhost" port 6112 (psock_connect: Connection refused)
bnstat: fatal error during handshake
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ bnstat
bnstat: could not connect to server "localhost" port 6112 (psock_connect: Connection refused)
bnstat: fatal error during handshake
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ 


Am going to assume that i need to open the ports ect ect right?

---

### Post by I WILL DO IT on 2009-09-12
IS it ok if i bump it?

---

### Post by DavidFromCanada on 2009-12-28
Was a solution found to this issue? Cause I have it too, when I compile from source and from apt-get.

---

