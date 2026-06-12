---
title: "problem compiling PvPGN SVN"
date: 2009-09-21
forum: Server Platforms
---

### Post by alanfake on 2009-09-21
mr@mr-desktop:~/trunk/pvpgn$ cmake -D CMAKE_INSTALL_PREFIX=/home/mr/ppvpgn -D WITH_MYSQL=true /home/mr/trunk/pvpgn

-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- pvpgn is used as APPLICATION_NAME
-- Found ZLIB: /usr/lib/libz.so
-- Looking for pcap_open_offline in pcap
-- Looking for pcap_open_offline in pcap - not found
-- Looking for gethostbyname in nsl
-- Looking for gethostbyname in nsl - found
-- Looking for socket in socket
-- Looking for socket in socket - not found
-- Looking for inet_aton in resolv
-- Looking for inet_aton in resolv - found
-- Looking for __inet_aton in bind
-- Looking for __inet_aton in bind - not found
-- Looked for MySQL libraries named mysqlclient;mysqlclient_r.
CMake Error at cmake/Modules/FindMySQL.cmake:60 (MESSAGE):
  Could NOT find MySQL library
Call Stack (most recent call first):
  ConfigureChecks.cmake:41 (find_package)
  CMakeLists.txt:29 (include)


-- Configuring incomplete, errors occurred!

Help plz!!..

---

### Post by alanfake on 2009-09-21
[SIZE=5][COLOR=Red]ERROR 2:[/COLOR][/SIZE]

mr@mr-desktop:~/trunk/pvpgn$ cmake -D CMAKE_INSTALL_PREFIX=/home/mr/ppvpgn -D WITH_MYSQL=[COLOR=Red]false[/COLOR] /home/mr/trunk/pvpgn

-- pvpgn is used as APPLICATION_NAME
-- Looking for include files HAVE_STD_HEADERS
-- Looking for include files HAVE_STD_HEADERS - found
-- Looking for C++ include fcntl.h
-- Looking for C++ include fcntl.h - found
-- Looking for C++ include sys/time.h
-- Looking for C++ include sys/time.h - found
-- Looking for C++ include sys/select.h
-- Looking for C++ include sys/select.h - found
-- Looking for C++ include unistd.h
-- Looking for C++ include unistd.h - found
-- Looking for C++ include sys/utsname.h
-- Looking for C++ include sys/utsname.h - found
-- Looking for C++ include sys/timeb.h
-- Looking for C++ include sys/timeb.h - found
-- Looking for C++ include sys/socket.h
-- Looking for C++ include sys/socket.h - found
-- Looking for C++ include sys/param.h
-- Looking for C++ include sys/param.h - found
-- Looking for C++ include netinet/in.h
-- Looking for C++ include netinet/in.h - found
-- Looking for C++ include arpa/inet.h
-- Looking for C++ include arpa/inet.h - found
-- Looking for C++ include netdb.h
-- Looking for C++ include netdb.h - found
-- Looking for C++ include termios.h
-- Looking for C++ include termios.h - found
-- Looking for C++ include sys/types.h
-- Looking for C++ include sys/types.h - found
-- Looking for C++ include sys/wait.h
-- Looking for C++ include sys/wait.h - found
-- Looking for C++ include sys/ioctl.h
-- Looking for C++ include sys/ioctl.h - found
-- Looking for C++ include stdint.h
-- Looking for C++ include stdint.h - found
-- Looking for C++ include sys/file.h
-- Looking for C++ include sys/file.h - found
-- Looking for C++ include poll.h
-- Looking for C++ include poll.h - found
-- Looking for C++ include sys/poll.h
-- Looking for C++ include sys/poll.h - found
-- Looking for C++ include sys/stropts.h
-- Looking for C++ include sys/stropts.h - found
-- Looking for C++ include sys/stat.h
-- Looking for C++ include sys/stat.h - found
-- Looking for C++ include pwd.h
-- Looking for C++ include pwd.h - found
-- Looking for C++ include grp.h
-- Looking for C++ include grp.h - found
-- Looking for C++ include dir.h
-- Looking for C++ include dir.h - not found
-- Looking for C++ include dirent.h
-- Looking for C++ include dirent.h - found
-- Looking for C++ include ndir.h
-- Looking for C++ include ndir.h - not found
-- Looking for C++ include sys/ndir.h
-- Looking for C++ include sys/ndir.h - not found
-- Looking for C++ include sys/dir.h
-- Looking for C++ include sys/dir.h - found
-- Looking for C++ include direct.h
-- Looking for C++ include direct.h - not found
-- Looking for C++ include sys/mman.h
-- Looking for C++ include sys/mman.h - found
-- Looking for include files HAVE_SYS_EVENT_H
-- Looking for include files HAVE_SYS_EVENT_H - not found.
-- Looking for C++ include sys/epoll.h
-- Looking for C++ include sys/epoll.h - found
-- Looking for C++ include sys/resource.h
-- Looking for C++ include sys/resource.h - found
-- Looking for C++ include pcap.h
-- Looking for C++ include pcap.h - not found
-- Looking for C++ include windows.h
-- Looking for C++ include windows.h - not found
-- Looking for C++ include winsock2.h
-- Looking for C++ include winsock2.h - not found
-- Looking for C++ include process.h
-- Looking for C++ include process.h - not found
-- Check size of unsigned char
-- Check size of unsigned char - done
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Check size of unsigned int
-- Check size of unsigned int - done
-- Check size of unsigned long
-- Check size of unsigned long - done
-- Check size of unsigned long long
-- Check size of unsigned long long - done
-- Check size of signed char
-- Check size of signed char - done
-- Check size of signed short
-- Check size of signed short - done
-- Check size of signed int
-- Check size of signed int - done
-- Check size of signed long
-- Check size of signed long - done
-- Check size of signed long long
-- Check size of signed long long - done
-- Looking for mmap
-- Looking for mmap - found
-- Looking for gettimeofday
-- Looking for gettimeofday - found
-- Looking for strdup
-- Looking for strdup - found
-- Looking for strtoul
-- Looking for strtoul - found
-- Looking for uname
-- Looking for uname - found
-- Looking for fork
-- Looking for fork - found
-- Looking for getpid
-- Looking for getpid - found
-- Looking for sigaction
-- Looking for sigaction - found
-- Looking for sigprocmask
-- Looking for sigprocmask - found
-- Looking for sigaddset
-- Looking for sigaddset - found
-- Looking for setpgid
-- Looking for setpgid - found
-- Looking for ftime
-- Looking for ftime - found
-- Looking for strcasecmp
-- Looking for strcasecmp - found
-- Looking for strncasecmp
-- Looking for strncasecmp - found
-- Looking for stricmp
-- Looking for stricmp - not found
-- Looking for strnicmp
-- Looking for strnicmp - not found
-- Looking for chdir
-- Looking for chdir - found
-- Looking for difftime
-- Looking for difftime - found
-- Looking for strchr
-- Looking for strchr - found
-- Looking for strrchr
-- Looking for strrchr - found
-- Looking for index
-- Looking for index - found
-- Looking for rindex
-- Looking for rindex - found
-- Looking for wait
-- Looking for wait - found
-- Looking for waitpid
-- Looking for waitpid - found
-- Looking for pipe
-- Looking for pipe - found
-- Looking for getenv
-- Looking for getenv - found
-- Looking for ioctl
-- Looking for ioctl - found
-- Looking for setsid
-- Looking for setsid - found
-- Looking for poll
-- Looking for poll - found
-- Looking for getlogin
-- Looking for getlogin - found
-- Looking for getpwnam
-- Looking for getpwnam - found
-- Looking for getgrnam
-- Looking for getgrnam - found
-- Looking for getuid
-- Looking for getuid - found
-- Looking for getgid
-- Looking for getgid - found
-- Looking for setuid
-- Looking for setuid - found
-- Looking for mkdir
-- Looking for mkdir - found
-- Looking for _mkdir
-- Looking for _mkdir - not found
-- Looking for strsep
-- Looking for strsep - found
-- Looking for getopt
-- Looking for getopt - found
-- Looking for kqueue
-- Looking for kqueue - not found
-- Looking for setitimer
-- Looking for setitimer - found
-- Looking for epoll_create
-- Looking for epoll_create - found
-- Looking for getrlimit
-- Looking for getrlimit - found
-- Looking for vsnprintf
-- Looking for vsnprintf - found
-- Looking for _vsnprintf
-- Looking for _vsnprintf - not found
-- Looking for snprintf
-- Looking for snprintf - found
-- Looking for _snprintf
-- Looking for _snprintf - not found
-- Looking for setpgrp
-- Looking for setpgrp - found
-- Looking for inet_aton
-- Looking for inet_aton - found
-- Looking for gethostname
-- Looking for gethostname - found
-- Looking for select
-- Looking for select - found
-- Looking for socket
-- Looking for socket - found
-- Looking for inet_ntoa
-- Looking for inet_ntoa - found
-- Looking for recv
-- Looking for recv - found
-- Looking for send
-- Looking for send - found
-- Looking for recvfrom
-- Looking for recvfrom - found
-- Looking for sendto
-- Looking for sendto - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for getservbyname
-- Looking for getservbyname - found
-- Checking for single argument mkdir MKDIR_TAKES_ONE_ARG
-- Checking for single argument mkdir MKDIR_TAKES_ONE_ARG - not found.
-- Performing Test WITH_FLAG_ANSIPEDANTIC
-- Performing Test WITH_FLAG_ANSIPEDANTIC - Success
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
MYSQL_INCLUDE_DIR
   used as include directory in directory /home/mr/trunk/pvpgn/src/bnetd

-- Configuring incomplete, errors occurred!

---

### Post by Bachstelze on 2009-09-21
You need libmysqlclient-dev.

---

### Post by Padakwaak on 2009-10-06
If you compile it with MySQL, make sure to install the MySQL client libraries.
I'm running Ubuntu 9.04 and the following fixed it:```
sudo apt-get install libmysqlclient15-dev
```

---

