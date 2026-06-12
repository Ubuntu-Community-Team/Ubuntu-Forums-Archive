---
title: "Itrepid~snort error in terminal !"
date: 2009-03-04
forum: Security
---

### Post by KEE on 2009-03-04
```
 sudo apt-get install snort-mysql
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libprelude2 oinkmaster snort-common snort-common-libraries
  snort-rules-default
Suggested packages:
  snort-doc
The following NEW packages will be installed:
  libprelude2 oinkmaster snort-common snort-common-libraries snort-mysql
  snort-rules-default
0 upgraded, 6 newly installed, 0 to remove and 6 not upgraded.
Need to get 1852kB of archives.
After this operation, 9449kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com intrepid/universe snort-common 2.7.0-19ubuntu1 [146kB]
Get:2 http://ca.archive.ubuntu.com intrepid-updates/universe libprelude2 0.9.17.2-1ubuntu1.1 [496kB]
Get:3 http://ca.archive.ubuntu.com intrepid/universe snort-common-libraries 2.7.0-19ubuntu1 [245kB]
Get:4 http://ca.archive.ubuntu.com intrepid/universe snort-rules-default 2.7.0-19ubuntu1 [398kB]
Get:5 http://ca.archive.ubuntu.com intrepid/universe snort-mysql 2.7.0-19ubuntu1 [475kB]
Get:6 http://ca.archive.ubuntu.com intrepid/universe oinkmaster 2.0-2 [92.0kB] 
Fetched 1852kB in 3min42s (8341B/s)                                            
Preconfiguring packages ...
Selecting previously deselected package snort-common.
(Reading database ... 119077 files and directories currently installed.)
Unpacking snort-common (from .../snort-common_2.7.0-19ubuntu1_all.deb) ...
Selecting previously deselected package libprelude2.
Unpacking libprelude2 (from .../libprelude2_0.9.17.2-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package snort-common-libraries.
Unpacking snort-common-libraries (from .../snort-common-libraries_2.7.0-19ubuntu1_i386.deb) ...
Selecting previously deselected package snort-rules-default.
Unpacking snort-rules-default (from .../snort-rules-default_2.7.0-19ubuntu1_all.deb) ...
Selecting previously deselected package snort-mysql.
Unpacking snort-mysql (from .../snort-mysql_2.7.0-19ubuntu1_i386.deb) ...
Selecting previously deselected package oinkmaster.
Unpacking oinkmaster (from .../oinkmaster_2.0-2_all.deb) ...
Processing triggers for man-db ...
Setting up snort-common (2.7.0-19ubuntu1) ...

Setting up libprelude2 (0.9.17.2-1ubuntu1.1) ...

Setting up snort-common-libraries (2.7.0-19ubuntu1) ...

Setting up snort-rules-default (2.7.0-19ubuntu1) ...
Setting up snort-mysql (2.7.0-19ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort                            * No running snort instance found
 * Starting Network Intrusion Detection System  snort                            * /etc/snort/db-pending-config file found
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort-mysql (--configure):
 subprocess post-installation script returned error exit status 6
Setting up oinkmaster (2.0-2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 snort-mysql
```

Please help

---

### Post by KEE on 2009-03-04
also this has popped up ```
The current Snort configuration is invalid and will prevent Snort starting up normally. Please review and correct it.

To diagnose an error in a Snort configuration file, use '/usr/sbin/snort -T -c <file>'.
```

---

### Post by KEE on 2009-03-04
```
E: snort: subprocess post-installation script returned error exit status 6
``` wow now im getting a crash report on snort =/

---

### Post by KEE on 2009-03-06
please help

---

### Post by dannyboy79 on 2009-03-06
did you read what it tells you to do?

Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config

also, are you using a guide for configuring snort? if so, which one?

---

### Post by bodhi.zazen on 2009-03-06
There is a sticky on these forums for how to install and configure snort.

Yes, that is compiling from source, but to be honest the version of snort in the repos is a bit out dated so it is not as if using the repos keeps you up to date.

IMO, for security apps, you should be a bit more up to date then the repos and to be honest it is not *that* hard to compile and install snort.

---

### Post by KEE on 2009-03-06
um is snort a purchased software? 

cause i cant get the set of rules [http://www.snort.org/pub-bin/downloads.cgi](http://www.snort.org/pub-bin/downloads.cgi) with my my current login subscription. there's a option in my profile that wants me to subscribe using my credit card =/

---

### Post by KEE on 2009-03-06
> **bodhi.zazen said:**
> There is a sticky on these forums for how to install and configure snort.

Yes, that is compiling from source, but to be honest the version of snort in the repos is a bit out dated so it is not as if using the repos keeps you up to date.

IMO, for security apps, you should be a bit more up to date then the repos and to be honest it is not *that* hard to compile and install snort.

ok i found a user verified option ;) but im locked out in getting ```
apt-get -y install build-essential libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev
```
i get this error 
```

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
***@***-desktop:~$ 
```
i believe i do have administration settings enabled but does this mean my current settings in repertoires is messed up? please help

---

### Post by cariboo on 2009-03-06
Do you have Synaptic or Add/Remove Programs running?

Jim

---

### Post by bodhi.zazen on 2009-03-06
> **cariboo907 said:**
> Do you have Synaptic or Add/Remove Programs running?

Jim

If you look at the command it appears he did not use sudo ;)

Otherwise what cariboo907 said :twisted:

---

### Post by KEE on 2009-03-07
> **bodhi.zazen said:**
> If you look at the command it appears he did not use sudo ;)

Otherwise what cariboo907 said :twisted:

in step 2 [http://ubuntuforums.org/showpost.php?p=5786055&postcount=2](http://ubuntuforums.org/showpost.php?p=5786055&postcount=2) under How to install snort + mysql + base  it says Obtain snort source code here [http://www.snort.org/](http://www.snort.org/).  Is the current one snortsp-3.0.0b2.tar.gz? what is the current one? i cant find "snort source code" in the search but forums threads only or is snort-2.8.3.tar.gz current?

```
cd /usr/src
wget http://www.snort.org/dl/snort-2.8.3.1.tar.gz && tar -zxvf snort-2.8.3.1.tar.gz
```
  ```
cd /usr/src
wget http://www.snort.org/dl/snort-2.8.3.tar.gz && tar -zxvf snort-2.8.3.tar.gz 

```
and ```
cd /usr/src
wget http://www.snort.org/dl/current/snortsp-3.0.0b2.tar.gz
tar zxvf snortsp-3.0.0b2.tar.gz
```

both give me 
```
***@***-desktop:~$ cd /usr/src
kirk@kirk-desktop:/usr/src$ wget http://www.snort.org/dl/*snortfile*.tar.gz && tar -zxvf *snortfile*.tar.gz 
--2009-03-07 00:42:10--  http://www.snort.org/dl/*snortfile*.tar.gz
Resolving www.snort.org... 68.177.102.20
Connecting to www.snort.org|68.177.102.20|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-07 00:42:17 ERROR 404: Not Found.

```



please and thanks again =)

---

### Post by KEE on 2009-03-07
double post

---

### Post by bodhi.zazen on 2009-03-07
go to the snort home page and follow the download or get snort tags ;)

---

### Post by KEE on 2009-03-07
> **bodhi.zazen said:**
> go to the snort home page and follow the download or get snort tags ;)

could you give me the name of file to it please? that would help thanks very much ;)

---

### Post by KEE on 2009-03-07
> **bodhi.zazen said:**
> go to the snort home page and follow the download or get snort tags ;)

snort-2.8.3.2.tar.gz i think thats it. could you confirm? sorry if being a little couscous.   i just dont want to do something wrong with network files :)

I also could not find a documentation on how to install or that i should compile from scratch?

```
sudo apt-get build-dep snort-2.8.3.2.tar.gz
``` 
 
need help with that too please and thank you =)

---

### Post by bodhi.zazen on 2009-03-07
go here : [http://www.snort.org/](http://www.snort.org/)

Click the really big button on the left "GET SNORT"

That takes you here : [http://www.snort.org/dl/](http://www.snort.org/dl/)

You will see, in big letters:

"Latest Snort Releases"

And right under that :

"**[B]Latest Production Snort Release (STABLE)**[/B]"

Which links to : [http://www.snort.org/dl/snort-2.8.3.2.tar.gz](http://www.snort.org/dl/snort-2.8.3.2.tar.gz)

I do not mean to be rude, but to be honest if you could not figure that out it almost begs the question, are you sure you are up to this project ?

---

### Post by KEE on 2009-03-07
> **bodhi.zazen said:**
> go here : [http://www.snort.org/](http://www.snort.org/)

Click the really big button on the left "GET SNORT"

That takes you here : [http://www.snort.org/dl/](http://www.snort.org/dl/)

You will see, in big letters:

"Latest Snort Releases"

And right under that :

"**[B]Latest Production Snort Release (STABLE)**[/B]"

Which links to : [http://www.snort.org/dl/snort-2.8.3.2.tar.gz](http://www.snort.org/dl/snort-2.8.3.2.tar.gz)

I do not mean to be rude, but to be honest if you could not figure that out it almost begs the question, are you sure you are up to this project ?

ok thanks 

is this how I cd it?
```
$cd ~/Desktop
```
```
$sudo root:root snort-2.8.3.2.tar.gz
```
```
$sudo cp snort-2.8.3.2.tar.gz /tmp
```
```
$ls -l
```
```
$sudo apt-get update && sudo apt-get install medibuntu-keyring
```
cant extract snort-2.8.3.2.tar.gz to /usr/src location.  need help please

---

### Post by bodhi.zazen on 2009-03-08
My only suggestion at this point is that you go back to this post :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

And perhaps try to follow it along.

---

### Post by KEE on 2009-03-08
> **bodhi.zazen said:**
> My only suggestion at this point is that you go back to this post :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

And perhaps try to follow it along.

right, i tried [http://ubuntuforums.org/showpost.php?p=5786055&postcount=2](http://ubuntuforums.org/showpost.php?p=5786055&postcount=2) but im stuck at #2 step. please and thank you 


also in the INSTALL readme, #2 says ./configure, but is that ```
sudo apt-get build-dep snort-2.8.3.2.tar.gz
``` not sure sure on ./configure code for snort-2.8.3.2.tar.gz and im not clear what to do after a have the snort-2.8.3.2.tar.gz in #2 of [http://ubuntuforums.org/showpost.php?p=5786055&postcount=2](http://ubuntuforums.org/showpost.php?p=5786055&postcount=2). please help and thanks

---

### Post by KEE on 2009-03-08
ok so i extracted the snort 2.8.3.2.tar.gz in /home/me/snort 2.8.3.2.tar.gz instead of usr/src cause I couldn't extract there. cant even do it with nautilus =/ 

```
cd /home/*/snort-2.8.3.2

```

```
*@*-desktop:~/snort-2.8.3.2$ ./configure -enable-dynamicplugin --with-mysql

```

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for ranlib... ranlib
checking for bison... bison
checking for flex... flex
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ranlib... (cached) ranlib
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether byte ordering is bigendian... no
checking for sparc alignment... no
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for inttypes.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking whether printf must be declared... no
checking whether fprintf must be declared... no
checking whether syslog must be declared... no
checking whether puts must be declared... no
checking whether fputs must be declared... no
checking whether fputc must be declared... no
checking whether fopen must be declared... no
checking whether fclose must be declared... no
checking whether fwrite must be declared... no
checking whether fflush must be declared... no
checking whether getopt must be declared... no
checking whether bzero must be declared... no
checking whether bcopy must be declared... no
checking whether memset must be declared... no
checking whether strtol must be declared... no
checking whether strcasecmp must be declared... no
checking whether strncasecmp must be declared... no
checking whether strerror must be declared... no
checking whether perror must be declared... no
checking whether socket must be declared... no
checking whether sendto must be declared... no
checking whether vsnprintf must be declared... no
checking whether snprintf must be declared... no
checking whether strtoul must be declared... no
checking for snprintf... yes
checking for strlcpy... no
checking for strlcat... no
checking for strerror... yes
checking for vswprintf... yes
checking for wprintf... yes
checking for sizeof(unsigned long)... 32 bits
checking for __FUNCTION__... yes
checking for floor in -lm... yes
checking for pcap_datalink in -lpcap... yes
checking for libpcap version >= 0.9... yes
checking for libpcap version 0.9.0 - 0.9.4... no
checking pcre.h usability... yes
checking pcre.h presence... yes
checking for pcre.h... yes
checking for pcre_compile in -lpcre... yes
checking for libpcre version 6.0 or greater... yes
checking for mysql... yes
checking for compress in -lz... yes
checking for dlsym in -ldl... yes
checking for u_int8_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for linuxthreads... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/sfutil/Makefile
config.status: creating src/detection-plugins/Makefile
config.status: creating src/dynamic-plugins/Makefile
config.status: creating src/dynamic-plugins/sf_engine/Makefile
config.status: creating src/dynamic-plugins/sf_engine/examples/Makefile
config.status: creating src/dynamic-plugins/sf_preproc_example/Makefile
config.status: creating src/dynamic-preprocessors/Makefile
config.status: creating src/dynamic-preprocessors/libs/Makefile
config.status: creating src/dynamic-preprocessors/ftptelnet/Makefile
config.status: creating src/dynamic-preprocessors/smtp/Makefile
config.status: creating src/dynamic-preprocessors/ssh/Makefile
config.status: creating src/dynamic-preprocessors/dcerpc/Makefile
config.status: creating src/dynamic-preprocessors/dns/Makefile
config.status: creating src/dynamic-examples/Makefile
config.status: creating src/dynamic-examples/dynamic-preprocessor/Makefile
config.status: creating src/dynamic-examples/dynamic-rule/Makefile
config.status: creating src/dynamic-preprocessors/ssl/Makefile
config.status: creating src/output-plugins/Makefile
config.status: creating src/preprocessors/Makefile
config.status: creating src/preprocessors/HttpInspect/Makefile
config.status: creating src/preprocessors/HttpInspect/include/Makefile
config.status: creating src/preprocessors/HttpInspect/utils/Makefile
config.status: creating src/preprocessors/HttpInspect/anomaly_detection/Makefile
config.status: creating src/preprocessors/HttpInspect/client/Makefile
config.status: creating src/preprocessors/HttpInspect/event_output/Makefile
config.status: creating src/preprocessors/HttpInspect/mode_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/normalization/Makefile
config.status: creating src/preprocessors/HttpInspect/server/Makefile
config.status: creating src/preprocessors/HttpInspect/session_inspection/Makefile
config.status: creating src/preprocessors/HttpInspect/user_interface/Makefile
config.status: creating src/preprocessors/flow/Makefile
config.status: creating src/preprocessors/flow/int-snort/Makefile
config.status: creating src/preprocessors/flow/portscan/Makefile
config.status: creating src/preprocessors/Stream5/Makefile
config.status: creating src/parser/Makefile
config.status: creating src/target-based/Makefile
config.status: creating doc/Makefile
config.status: creating contrib/Makefile
config.status: creating schemas/Makefile
config.status: creating rpm/Makefile
config.status: creating preproc_rules/Makefile
config.status: creating m4/Makefile
config.status: creating etc/Makefile
config.status: creating templates/Makefile
config.status: creating src/win32/Makefile
config.status: creating config.h
config.status: executing depfiles commands



```
```
*@*-desktop:~/snort-2.8.3.2$ make

```then this error shows up
```
g -O2 -Wall -DDYNAMIC_PLUGIN -DDETECTION_OPTION_TREE -fno-strict-aliasing -c server_stats.c
In function ‘open’,
    inlined from ‘server_stats_save’ at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[5]: *** [server_stats.o] Error 1
make[5]: Leaving directory `/home/*/snort-2.8.3.2/src/preprocessors/flow/portscan'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/*/snort-2.8.3.2/src/preprocessors/flow'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/*/snort-2.8.3.2/src/preprocessors'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/*/snort-2.8.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/*/snort-2.8.3.2'
make: *** [all] Error 2

```
is this normal??

---

### Post by KEE on 2009-03-08
need help! please and thank you

---

### Post by KEE on 2009-03-08
```
g -O2 -Wall -DDYNAMIC_PLUGIN -DDETECTION_OPTION_TREE -fno-strict-aliasing -c server_stats.c
In function &#8216;open&#8217;,
    inlined from &#8216;server_stats_save&#8217; at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[5]: *** [server_stats.o] Error 1
make[5]: Leaving directory `/usr/src/snort-2.8.3.2/src/preprocessors/flow/portscan'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.2/src/preprocessors/flow'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3.2/src/preprocessors'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.2'
make: *** [all] Error 2
```

tried a few things, i got nautilus to work this time and snort-2.8.3.2 is in usr/src now but i still get the same errors =/ for snort rules, im using /usr/src/snortrules-snapshot-CURRENT also. anyway need help =)

---

### Post by KEE on 2009-03-08
please help someone and thank you

---

### Post by bodhi.zazen on 2009-03-09
[http://ubuntuforums.org/showthread.php?t=1040886](http://ubuntuforums.org/showthread.php?t=1040886)

---

### Post by KEE on 2009-03-09
> **bodhi.zazen said:**
> [http://ubuntuforums.org/showthread.php?t=1040886](http://ubuntuforums.org/showthread.php?t=1040886)

didnt work =/ 
```
<path_to_snort_source>/src/preprocessors/flow/portscan/server_stats.c
```

changed the code and only found one text line underneath the code text /* open this description, create it if necessary, always wait on
     * sync to disk w/ every write, only write */ ```
fd = open(filename, O_CREAT|O_TRUNC|O_SYNC|O_WRONLY);
```

anyway changed that to ```
fd = open(filename, O_CREAT, S_IRUSR|S_IWUSR|O_TRUNC|O_SYNC|O_WRONLY);
```

here's the text document changed```
/****************************************************************************
 *
 * Copyright (C) 2003-2008 Sourcefire, Inc.
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License Version 2 as
 * published by the Free Software Foundation.  You may not use, modify or
 * distribute this program under any other version of the GNU General
 * Public License.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
 *
 ****************************************************************************/
 
/**
 * @file   server_stats.c
 * @author Chris Green <cmg@sourcefire.com>
 * @date   Fri Jun 13 14:28:50 2003
 * 
 * @brief  "policy" learning portion of portscan detector
 * 
 * This keeps a table of (dip+dport+dprotocol) -> count to help
 * identify what is a normal looking portscan versus what is pretty
 * far outta whack.
 *
 */

#include "server_stats.h"
#include "flowps.h"
#include "sfxhash.h"

#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h> 
#include <string.h>

static void server_stats_init_entry(void);

typedef struct _SERVER_KEY
{
    u_int32_t address;
    u_int32_t port;
    u_int32_t protocol;  
} SERVER_KEY;

static SERVER_KEY s_key; 
static int s_debug = 0;

/** 
 * Print out the entirety of the server cache.
 * 
 * @param ssp server stats pointer
 */
void server_stats_dump(SERVER_STATS *ssp)
{
    SFXHASH_NODE *nodep;
    
    if(ssp && ssp->ipv4_table)
    {
        for( nodep = sfxhash_ghead(ssp->ipv4_table);
             nodep != NULL;
             nodep = sfxhash_gnext(nodep) )
        {
            SERVER_KEY *kp = (SERVER_KEY *) nodep->key;
            u_int32_t count = *(u_int32_t *) nodep->data;
            
            flow_printf("hits: %u proto: %3u port: %5u ip: %s\n",
                        count,
                        kp->protocol,
                        kp->port,
                        inet_ntoa(*(struct in_addr *)&kp->address));
        }
    }
    else
    {
        flow_printf("nothing to dump!\n");
    }
}

void server_stats(SERVER_STATS *ssp, int dumpall)
{
    unsigned total, fail, success, nodes, anr, overhead, memcap;

    memcap = overhead = nodes = anr = total = fail = success = 0;
    
    if(ssp && ssp->ipv4_table)
    {
        total    = sfxhash_find_total(ssp->ipv4_table);
        fail     = sfxhash_find_fail(ssp->ipv4_table);
        success  = sfxhash_find_success(ssp->ipv4_table);
        nodes    = sfxhash_count(ssp->ipv4_table);
        anr      = sfxhash_anr_count(ssp->ipv4_table);
        memcap   = server_stats_memcap(ssp);
        overhead = server_stats_overhead_bytes(ssp);
    }    

    flow_printf(",-----[SERVER STATS]------------\n");
    flow_printf("   Memcap: %u  Overhead Bytes: %u\n",
                memcap, overhead);
    
    flow_printf("   Finds: %u (Sucessful: %u(%%%f) Unsucessful: %u(%%%f))\n",
                total,
                success, calc_percent(success,total),
                fail, calc_percent(fail,total));

    flow_printf("   Nodes: %u\n", nodes);
    
    flow_printf("   Recovered Nodes: %u\n", anr);
    flow_printf("`-------------------------------\n");

    if(dumpall)
        server_stats_dump(ssp);
}

/** 
 * Initialize the server stats structure
 *
 * If we do not specify a watchnet, then we have no use for this
 * structure
 * 
 * @param ssp server stats structure to initialize
 * @param watchnet what network we're watching for information
 * @param rows how many rows the underlying table should use
 * @param memcap what our total memory limit is
 * 
 * @return FLOW_SUCCESS on success
 */
int server_stats_init(SERVER_STATS *ssp, IPSET *watchnetv4,
                      unsigned int rows, int memcap)
{
    if(!ssp || !watchnetv4)
        return FLOW_ENULL;

    server_stats_init_entry();
    
    memset(ssp, 0, sizeof(SERVER_STATS));

    
    if(ipset_family(watchnetv4) != IPV4_FAMILY)
    {
        return FLOW_EINVALID;
    }

    /* what size should we do? */
    ssp->ipv4_table = sfxhash_new(rows,               /* # of rows in HT*/
                                  sizeof(SERVER_KEY), /* size of the key  */
                                  sizeof(u_int32_t),   /* data size */
                                  memcap,            /* how much memory is alloted */
                                  1,                 /* auto recover nodes */
                                  NULL,              /* autorecovery function */
                                  NULL,              /* free function for the data */
                                  1);                /* recycle old nodes */

    if(ssp->ipv4_table == NULL)
    {
        return FLOW_ENOMEM;
    }

    ssp->ipv4_watch = ipset_copy(watchnetv4);
    
    if(!ssp->ipv4_watch)
    {
        sfxhash_delete(ssp->ipv4_table);        
        return FLOW_ENOMEM;
    }

    return FLOW_SUCCESS;
}

int server_stats_destroy(SERVER_STATS *ssp)
{
    if(!ssp)
    {
        return FLOW_ENULL;
    }
    
    sfxhash_delete(ssp->ipv4_table);
    ipset_free(ssp->ipv4_watch);

    return FLOW_SUCCESS;
}

/** 
 * See if we are watching this particular IP 
 * 
 * @param ssp server stats pointer
 * @param address ipv4 address in NETWORK BYTE ORDER
 * 
 * @return 1 if this SERVER_STATS is watching this network
 */
int server_stats_contains(SERVER_STATS *ssp, u_int32_t address)
{
    if(ssp->ipv4_watch)
    {
        u_int32_t hostaddress = ntohl(address);

        if(ipset_contains(ssp->ipv4_watch, &hostaddress, NULL, IPV4_FAMILY))
        {
            return FLOW_SUCCESS;
        }
    }
    
    return FLOW_DISABLED;        
}


u_int32_t server_stats_hitcount_ipv4(SERVER_STATS *ssp, u_int8_t ip_proto, u_int32_t address, u_int16_t port)
{
    SERVER_KEY *kp = &s_key;
    u_int32_t *hitcountp;
#ifdef DEBUG
    u_int32_t hostaddress = ntohl(address);
#endif /* DEBUG */

    /* OK, IPSETs are acting in HOST ORDER */
    FLOWASSERT(ipset_contains(ssp->ipv4_watch, &hostaddress, NULL, IPV4_FAMILY));

    /* make a key */
    kp->address = address;
    kp->port = port;
    kp->protocol = ip_proto;
    
    hitcountp = (u_int32_t *) sfxhash_find(ssp->ipv4_table, kp);
    
    if(hitcountp != NULL)
    {
        return *hitcountp;
    }

    return 0;    
}

int server_stats_add_ipv4(SERVER_STATS *ssp, u_int8_t ip_proto, u_int32_t address, u_int16_t port,
                          u_int32_t *retcount)
{
    SERVER_KEY *kp = &s_key;
    u_int32_t one = 1;
    u_int32_t *hitcountp = NULL;
    int ret;
#ifdef DEBUG
    u_int32_t hostaddress = ntohl(address);
#endif /* DEBUG */
    
    if(ssp == NULL || retcount == NULL)
        return FLOW_ENULL;

    /* calls to this subsystem should only be made if we are really watching this. */
    FLOWASSERT(ipset_contains(ssp->ipv4_watch, &hostaddress, NULL, IPV4_FAMILY));
    
    /* make the key */
    kp->address  = address;
    kp->port     = port;
    kp->protocol = ip_proto;
    
    /* find the key, add 1 to it or add a new node to the table */
    ret = sfxhash_add(ssp->ipv4_table, kp, &one);
    
    switch(ret)
    {
    case SFXHASH_NOMEM:
        /* NOMEM means that we would add it if we could but we're
         *  hard-core out of space.  So, just assume we added it.
         */
    case SFXHASH_OK:
        *retcount = 1;        
        break;
    case SFXHASH_INTABLE:
        hitcountp = (u_int32_t *) sfxhash_mru(ssp->ipv4_table);
        
        /* never let us wrap around to less hits */
        if(!hitcountp)
        {
            /* this is an odd error! */
            return FLOW_BADJUJU;
        }
        else
        {
            if((*hitcountp) < SERVER_STATS_MAX_HITCOUNT)
            {
                (*hitcountp)++;
            }            
        }
        break;
    }
    
    return FLOW_SUCCESS;
}

int server_stats_remove_ipv4(SERVER_STATS *ssp, u_int8_t ip_proto,
                             u_int32_t address, u_int16_t port)
{
    SERVER_KEY *kp = &s_key;

    if(!ssp)
        return FLOW_ENULL;
       
    kp->address = address;
    kp->port = port;
    kp->protocol = ip_proto;

    /* not like we can do anything if this failed */
    sfxhash_remove(ssp->ipv4_table, kp);

    return FLOW_SUCCESS;
}


/* start of parsing helpers */
#define FAMILY_SIZE     1
#define FAMILY_OFFSET   0

#define IPV4_SIZE       4
#define IPV4_OFFSET     (FAMILY_SIZE)

#define PORT_SIZE       2
#define PORT_OFFSET     (IPV4_OFFSET + IPV4_SIZE)

#define IP_PROTO_SIZE   1
#define IP_PROTO_OFFSET (PORT_OFFSET + PORT_SIZE)

#define COUNT_SIZE      4
#define COUNT_OFFSET    (IP_PROTO_OFFSET + IP_PROTO_SIZE)

#define STATSREC_SIZE (FAMILY_SIZE + IPV4_SIZE + PORT_SIZE + IP_PROTO_SIZE + COUNT_SIZE)
/* end parsing helpers */

int server_stats_save(SERVER_STATS *ssp, char *filename)
{
    SFXHASH_NODE *nodep;
    unsigned char buf[STATSREC_SIZE];
    int fd;
    
    if(!filename || !ssp)
        return FLOW_ENULL;
#ifndef O_SYNC
#define O_SYNC O_FSYNC
#endif

    /* open this description, create it if necessary, always wait on
     * sync to disk w/ every write, only write */
    fd = open(filename, O_CREAT, S_IRUSR|S_IWUSR|O_TRUNC|O_SYNC|O_WRONLY);

    if(fd < 0)
    {
        if(s_debug)
        {
            flow_printf("%s was not found\n", filename);
        }
        return FLOW_NOTFOUND;
    }

    /* this is a crappy parser... that's par for the course */
    for( nodep = sfxhash_ghead(ssp->ipv4_table);
         nodep != NULL;
         nodep = sfxhash_gnext(nodep) )
    {
        SERVER_KEY *kp = (SERVER_KEY *) nodep->key;
        u_int32_t count = *(u_int32_t *) nodep->data;
        u_int8_t  family = '4';
        u_int32_t ipv4_address;
        u_int16_t port;
        u_int8_t  protocol;
        ssize_t  wbytes = 0;
        ssize_t wsize;
            
        
        count        = ntohl(count);       
        ipv4_address = htonl(kp->address);
        port         = htons((u_int16_t) kp->port);
        protocol     = (u_int8_t) kp->protocol;

        memcpy(buf + FAMILY_OFFSET,   &family,        FAMILY_SIZE);
        memcpy(buf + IPV4_OFFSET,     &ipv4_address,  IPV4_SIZE);       
        memcpy(buf + PORT_OFFSET,     &port,          PORT_SIZE);
        memcpy(buf + IP_PROTO_OFFSET, &protocol,      IP_PROTO_SIZE);
        memcpy(buf + COUNT_OFFSET,    &count,         COUNT_SIZE);

        /* now make sure we get a full record on disk */
        while(wbytes < STATSREC_SIZE)
        {
            /* write the number of bytes we already have - the #
             * already written */
            wsize = write(fd, buf, (STATSREC_SIZE - wbytes));

            if(wsize < 0)
            {
                /* this record was truncated */
                flow_printf("Truncated Server Record!\n");
                return FLOW_EINVALID;
            }
            else
            {
                wbytes += wsize;
            }
        }
    }
    
    return FLOW_SUCCESS;
}


/** 
 * initialize the static s_init_key variable once and only once.This
 * is used to zero out the key so that if the compiler pads the
 * structure, we still have 0's in this keylookup.
 * 
 */
static void server_stats_init_entry(void)
{
    static int init_once = 1;

    if(init_once)
    {
        init_once = 0;
        memset(&s_key, 0, sizeof(SERVER_KEY));
    }
}


/** 
 * get the memcap
 * 
 * @param sbp server_stats ptr to return the memcap of
 * 
 * @return memcap or -1
 */
int server_stats_memcap(SERVER_STATS *sbp)
{
    if(sbp != NULL && sbp->ipv4_table != NULL)        
        return sbp->ipv4_table->mc.memcap;

    return -1;            
}

/** 
 * get the node count
 * 
 * @param sbp server_stats ptr to return the memcap of
 * 
 * @return nrows or -1
 */
int server_stats_row_count(SERVER_STATS *sbp)
{
    if(sbp != NULL && sbp->ipv4_table != NULL)        
        return sbp->ipv4_table->nrows;

    return -1;            
}


/** 
 * get the overhead # of bytes
 * 
 * @param sbp server_stats ptr to return the memcap of
 * 
 * @return nrows or -1
 */
int server_stats_overhead_bytes(SERVER_STATS *sbp)
{
    if(sbp != NULL && sbp->ipv4_table != NULL)
        return sfxhash_overhead_bytes(sbp->ipv4_table);

    return -1;            
}


```
and here's the errors again in terminal 
```
make[6]: *** [install-libLTLIBRARIES] Error 1
make[6]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[5]: *** [install-am] Error 2
make[5]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/src'
make: *** [install-recursive] Error 1

```thanks but still stuck =( please help and thank you

---

### Post by KEE on 2009-03-09
gona try this code of text instead```
fd = open(filename, O_CREAT, S_IRUSR|S_IWUSR|O_TRUNC|O_SYNC|O_WRONLY); 
```

---

### Post by KEE on 2009-03-09
nope ```
/bin/mkdir: cannot create directory `/usr/local/lib/snort_dynamicengine': Permission denied
make[6]: *** [install-libLTLIBRARIES] Error 1
make[6]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[5]: *** [install-am] Error 2
make[5]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins/sf_engine'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/src/dynamic-plugins'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/src'
make: *** [install-recursive] Error 1


``` ok so get permission denied so i need help again and thank you. so close =)   write back soon  --edit, i left the little top part of the error *where it seems to go wrong =/

---

### Post by KEE on 2009-03-09
still need help please and thank you =)

---

### Post by bodhi.zazen on 2009-03-09
Although you should not need to, try running make as root (looks like a permissions problem).

sudo make
sudo make install

---

### Post by KEE on 2009-03-09
> **bodhi.zazen said:**
> Although you should not need to, try running make as root (looks like a permissions problem).

sudo make
sudo make install

oh ok thats doing more then it was before, however there alot "leaving" going on...im gona post it and could you let me no if it installed properly ```
test -z "/usr/local/share/doc/snort" || /bin/mkdir -p "/usr/local/share/doc/snort"
 /usr/bin/install -c -m 644 'AUTHORS' '/usr/local/share/doc/snort/AUTHORS'
 /usr/bin/install -c -m 644 'BUGS' '/usr/local/share/doc/snort/BUGS'
 /usr/bin/install -c -m 644 'CREDITS' '/usr/local/share/doc/snort/CREDITS'
 /usr/bin/install -c -m 644 'generators' '/usr/local/share/doc/snort/generators'
 /usr/bin/install -c -m 644 'INSTALL' '/usr/local/share/doc/snort/INSTALL'
 /usr/bin/install -c -m 644 'NEWS' '/usr/local/share/doc/snort/NEWS'
 /usr/bin/install -c -m 644 'PROBLEMS' '/usr/local/share/doc/snort/PROBLEMS'
 /usr/bin/install -c -m 644 'README' '/usr/local/share/doc/snort/README'
 /usr/bin/install -c -m 644 'README.alert_order' '/usr/local/share/doc/snort/README.alert_order'
 /usr/bin/install -c -m 644 'README.ARUBA' '/usr/local/share/doc/snort/README.ARUBA'
 /usr/bin/install -c -m 644 'README.asn1' '/usr/local/share/doc/snort/README.asn1'
 /usr/bin/install -c -m 644 'README.csv' '/usr/local/share/doc/snort/README.csv'
 /usr/bin/install -c -m 644 'README.database' '/usr/local/share/doc/snort/README.database'
 /usr/bin/install -c -m 644 'README.dcerpc' '/usr/local/share/doc/snort/README.dcerpc'
 /usr/bin/install -c -m 644 'README.decode' '/usr/local/share/doc/snort/README.decode'
 /usr/bin/install -c -m 644 'README.decoder_preproc_rules' '/usr/local/share/doc/snort/README.decoder_preproc_rules'
 /usr/bin/install -c -m 644 'README.dns' '/usr/local/share/doc/snort/README.dns'
 /usr/bin/install -c -m 644 'README.event_queue' '/usr/local/share/doc/snort/README.event_queue'
 /usr/bin/install -c -m 644 'README.FLEXRESP' '/usr/local/share/doc/snort/README.FLEXRESP'
 /usr/bin/install -c -m 644 'README.FLEXRESP2' '/usr/local/share/doc/snort/README.FLEXRESP2'
 /usr/bin/install -c -m 644 'README.flow' '/usr/local/share/doc/snort/README.flow'
 /usr/bin/install -c -m 644 'README.flowbits' '/usr/local/share/doc/snort/README.flowbits'
 /usr/bin/install -c -m 644 'README.flow-portscan' '/usr/local/share/doc/snort/README.flow-portscan'
 /usr/bin/install -c -m 644 'README.frag3' '/usr/local/share/doc/snort/README.frag3'
 /usr/bin/install -c -m 644 'README.ftptelnet' '/usr/local/share/doc/snort/README.ftptelnet'
 /usr/bin/install -c -m 644 'README.gre' '/usr/local/share/doc/snort/README.gre'
 /usr/bin/install -c -m 644 'README.http_inspect' '/usr/local/share/doc/snort/README.http_inspect'
 /usr/bin/install -c -m 644 'README.INLINE' '/usr/local/share/doc/snort/README.INLINE'
 /usr/bin/install -c -m 644 'README.ipip' '/usr/local/share/doc/snort/README.ipip'
 /usr/bin/install -c -m 644 'README.ipv6' '/usr/local/share/doc/snort/README.ipv6'
 /usr/bin/install -c -m 644 'README.pcap_readmode' '/usr/local/share/doc/snort/README.pcap_readmode'
 /usr/bin/install -c -m 644 'README.PerfProfiling' '/usr/local/share/doc/snort/README.PerfProfiling'
 /usr/bin/install -c -m 644 'README.PLUGINS' '/usr/local/share/doc/snort/README.PLUGINS'
 /usr/bin/install -c -m 644 'README.ppm' '/usr/local/share/doc/snort/README.ppm'
 /usr/bin/install -c -m 644 'README.sfportscan' '/usr/local/share/doc/snort/README.sfportscan'
 /usr/bin/install -c -m 644 'README.SMTP' '/usr/local/share/doc/snort/README.SMTP'
 /usr/bin/install -c -m 644 'README.ssh' '/usr/local/share/doc/snort/README.ssh'
 /usr/bin/install -c -m 644 'README.ssl' '/usr/local/share/doc/snort/README.ssl'
 /usr/bin/install -c -m 644 'README.stream4' '/usr/local/share/doc/snort/README.stream4'
 /usr/bin/install -c -m 644 'README.stream5' '/usr/local/share/doc/snort/README.stream5'
 /usr/bin/install -c -m 644 'README.tag' '/usr/local/share/doc/snort/README.tag'
 /usr/bin/install -c -m 644 'README.thresholding' '/usr/local/share/doc/snort/README.thresholding'
 /usr/bin/install -c -m 644 'README.UNSOCK' '/usr/local/share/doc/snort/README.UNSOCK'
 /usr/bin/install -c -m 644 'README.variables' '/usr/local/share/doc/snort/README.variables'
 /usr/bin/install -c -m 644 'README.WIN32' '/usr/local/share/doc/snort/README.WIN32'
 /usr/bin/install -c -m 644 'README.wireless' '/usr/local/share/doc/snort/README.wireless'
 /usr/bin/install -c -m 644 'TODO' '/usr/local/share/doc/snort/TODO'
 /usr/bin/install -c -m 644 'USAGE' '/usr/local/share/doc/snort/USAGE'
 /usr/bin/install -c -m 644 'WISHLIST' '/usr/local/share/doc/snort/WISHLIST'
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/doc'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/doc'
Making install in etc
make[1]: Entering directory `/usr/src/snort-2.8.3.2/etc'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/etc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/etc'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/etc'
Making install in templates
make[1]: Entering directory `/usr/src/snort-2.8.3.2/templates'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/templates'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/templates'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/templates'
Making install in contrib
make[1]: Entering directory `/usr/src/snort-2.8.3.2/contrib'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/contrib'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/contrib'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/contrib'
Making install in schemas
make[1]: Entering directory `/usr/src/snort-2.8.3.2/schemas'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/schemas'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/schemas'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/schemas'
Making install in rpm
make[1]: Entering directory `/usr/src/snort-2.8.3.2/rpm'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/rpm'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/rpm'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/rpm'
Making install in m4
make[1]: Entering directory `/usr/src/snort-2.8.3.2/m4'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/m4'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/m4'
Making install in preproc_rules
make[1]: Entering directory `/usr/src/snort-2.8.3.2/preproc_rules'
make[2]: Entering directory `/usr/src/snort-2.8.3.2/preproc_rules'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/snort-2.8.3.2/preproc_rules'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2/preproc_rules'
make[1]: Entering directory `/usr/src/snort-2.8.3.2'
make[2]: Entering directory `/usr/src/snort-2.8.3.2'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 './snort.8' '/usr/local/share/man/man8/snort.8'
make[2]: Leaving directory `/usr/src/snort-2.8.3.2'
make[1]: Leaving directory `/usr/src/snort-2.8.3.2'
***@***-desktop:/usr/src/snort-2.8.3.2$ 
```

---

### Post by KEE on 2009-03-09
well i went ahead (crossing fingers) and made it to "Configure snort" link. i have just few questions for now. How do rename sort database? is that done in terminal or just simply go ahead and rename /usr/src/snort-2.8.3.2 to /usr/src/sniff ? also same question for mysql user and the name of snort_password. =)write back soon

---

### Post by KEE on 2009-03-10
```
**@**-desktop:~$ mysql -D snort -u snort -p < /usr/src/snort-2.8.3.2/schemas/create_mysql

Enter password: 
ERROR 1045 (28000): Access denied for user 'snort'@'localhost' (using password: YES)
 
``` hmm stuck again please help and thank you =)

---

### Post by KEE on 2009-03-10
please help =(

---

### Post by KEE on 2009-03-10
```
**@**-desktop:/usr/src/snort-2.8.3.2$ cd /usr/src/snort-2.8.3.2
**@**-desktop:/usr/src/snort-2.8.3.2$ mkdir -p /etc/snort/rules /var/log/snort
mkdir: cannot create directory `/etc/snort/rules': Permission denied
mkdir: cannot create directory `/var/log/snort': Permission denied
**@**-desktop:/usr/src/snort-2.8.3.2$ 
```
 i almost skipped a couple of steps cause they dont workout using "sudo" or it would get denied for example*```
sudo adduser snort
``` ```
sudo chsh snort
``````
sudo passwd snort -l
``` anyway these following codes are not working at all, i have  /usr/src/snortrules-snapshot-CURRENT.tar.gz  btw couldnt find any rules other then those types, anyway these from the configuring step ```
cd /usr/src/snort-2.8.3.2
mkdir -p /etc/snort/rules /var/log/snort
chown -R root.snort /var/log/snort
chmod -R 770 /var/log/snort
cp etc/* /etc/snort/
cp rules/* /etc/snort/rules
``` need help or someone just tell me this is not going to work =/

so far they only work with sudo but the second last part ```
**@**-desktop:~$ cd /usr/src/snort-2.8.3.2
**@**-desktop:/usr/src/snort-2.8.3.2$ sudo mkdir -p /etc/snort/rules /var/log/snort
[sudo] password for **: 
**@**-desktop:/usr/src/snort-2.8.3.2$ sudo chown -R root.snort /var/log/snort
**@**-desktop:/usr/src/snort-2.8.3.2$ sudo chmod -R 770 /var/log/snort
**@**-desktop:/usr/src/snort-2.8.3.2$ cp etc/* /etc/snort/
cp: cannot create regular file `/etc/snort/attribute_table.dtd': Permission denied
cp: cannot create regular file `/etc/snort/classification.config': Permission denied
cp: cannot create regular file `/etc/snort/gen-msg.map': Permission denied
cp: cannot create regular file `/etc/snort/Makefile': Permission denied
cp: cannot create regular file `/etc/snort/Makefile.am': Permission denied
cp: cannot create regular file `/etc/snort/Makefile.in': Permission denied
cp: cannot create regular file `/etc/snort/reference.config': Permission denied
cp: cannot create regular file `/etc/snort/sid-msg.map': Permission denied
cp: cannot create regular file `/etc/snort/snort.conf': Permission denied
cp: cannot create regular file `/etc/snort/threshold.conf': Permission denied
cp: cannot create regular file `/etc/snort/unicode.map': Permission denied
**@**-desktop:/usr/src/snort-2.8.3.2$ 
```

---

### Post by KEE on 2009-03-10
yea so if I done anything wrong just say so. and i still need help please and thanks

---

### Post by bodhi.zazen on 2009-03-10
Keep following the how to I gave you.

For some reason you keep running commands without sudo and the permissions errors seem to confuse you.

These commands, for the most part, need to be run as root.

So sudo <command> 

Or become root with 

sudo -i

When you see a permission denied error you need to remember to use sudo ...

The only other problems I see are that you seem to get distracted and skip steps or take unnecessary steps. You need to make a user "snort" on your system , and a group snort on your system, and you need to add that user to mysql.

The instructions, however, are all in the how to.

Next will be to install base :twisted:

---

### Post by KEE on 2009-03-10
im actually gona quit there's no way im installing snort-2.8.3.2. for 1  theres no /rules in those files ?!?! and i cant make it with out errors so going to go back to what everyone has > 2.8.3 =) what rules did you use that wasnt so much trouble?

---

### Post by bodhi.zazen on 2009-03-10
I use the rules you download for snort, I registered so they are reasonably up to date.

---

### Post by KEE on 2009-03-10
ok so going try to use sudo -i first before anything and restart this =)

---

### Post by KEE on 2009-03-10
ok everything worked with sudo -i =D but got stuck here in the Configure snort```
root@me-desktop:/usr/src/snort-2.8.3.2# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database snortme;
    ->

```im just not sure how to fill this in =/ ```
grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password';
```
is this rewritten for myself? user <me> new snort name <snortme> ```
grant all privileges on snort.snortme to 'snort'@'me' identified by 'snort_password';
```please help and big thanks for for the help =D

---

### Post by bodhi.zazen on 2009-03-10
That is mysql

the user for mysql is NOT the same for the user for the system.

so you need a mysql data base, user, and password

database = snortme

user = snort or ?

password = give the user a password

grant all privileges on snortme.* to 'snort'@'localhost' identified by 'snort_password';
Change "snort" to the user name
Change "snort_password" to the password you wish to use

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> That is mysql

the user for mysql is NOT the same for the user for the system.

so you need a mysql data base, user, and password

database = snortme

user = snort or ?

password = give the user a password

grant all privileges on snortme.* to 'snort'@'localhost' identified by 'snort_password';
Change "snort" to the user name
Change "snort_password" to the password you wish to use

```
root@me-desktop:/usr/src/snort-2.8.3.2# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create 'snortme snort;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'snortme snort' at line 1
mysql> 

``` hm not sure whats going on =/

---

### Post by bodhi.zazen on 2009-03-10
mysql is very exacting on it's syntax.

Go back to this post :

[http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)

And follow the syntax :twisted:

change the variables to what you will for the name of the data base, user, and password.

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> mysql is very exacting on it's syntax.

Go back to this post :

[http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)

And follow the syntax :twisted:

change the variables to what you will for the name of the data base, user, and password.

ok, ubuntu user ( i think thats 'localhost')= me
new database=sniffme
snortpassword = password
ok so ```
->create database sniffme;
 ->grant all privileges on snort.* to sniffme@me identified by password; 

```
i tried it and got this, but im not in root anymore maybe thats whats wrong ```
me@me-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 18
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database sniffme;
Query OK, 1 row affected (0.12 sec)

mysql> grant all privileges on snort.* to sniffme@me identified by password; 
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'password' at line 1
mysql> 

```

---

### Post by bodhi.zazen on 2009-03-10
:lolflag:
[FONT=monospace]
[/FONT]Syntax is :

grant all privileges on "database_name".* to mysql_user_name@localhost identified by My_sql_user's_password;[FONT=monospace] 

[/FONT]So, I can fill in *some* of the blanks :

```
grant all privileges on sniffme.* to 'user_name'@'localhost' identified by 'password';
```

You told me everything but  the user_name

Also take note of the syntax. Notice the use of single quotes around certain parts ? And the ; at the end ?

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> :lolflag:
[FONT=monospace]
[/FONT]Syntax is :

grant all privileges on "database_name".* to mysql_user_name@localhost identified by My_sql_user's_password;[FONT=monospace] 

[/FONT]So, I can fill in *some* of the blanks :

```
grant all privileges on sniffme.* to 'user_name'@'localhost' identified by 'password';
```

You told me everything but  the user_name

Also take note of the syntax. Notice the use of single quotes around certain parts ? And the ; at the end ?

hehe k XD```
me@me-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 20
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database sniffme;
ERROR 1007 (HY000): Can't create database 'sniffme'; database exists
mysql> grant all privileges on sniffme.* to 'me'@'me' identified by 'password';
Query OK, 0 rows affected (0.50 sec)

mysql> exit
Bye
me@me-desktop:~$ 

``` thanks a bunch!!! Ill let ya know if I come across any more problems no doubt =D

---

### Post by KEE on 2009-03-10
what about this part? how would i fill in this ? ```
mysql -D snort -u snort -p < /usr/src/snort-2.8.3/schemas/create_mysql
```
i tried this but i get an error user_name=me , database=sniffme 
```
me@me-desktop:~$ mysql -D snort -u snort -p < /usr/src/snort-2.8.3/schemas/create_mysql
Enter password: 
ERROR 1045 (28000): Access denied for user 'snort'@'localhost' (using password: YES)
me@me-desktop:~$ mysql -D sniffme -u me -p < /usr/src/snort-2.8.3/schemas/create_mysql
Enter password: 
ERROR 1045 (28000): Access denied for user 'me'@'localhost' (using password: YES)
me@kme-desktop:~$ 

```please and thank you  =)

---

### Post by bodhi.zazen on 2009-03-10
-D snifme -u mysql_user_name

You have not told me the user name you entered in the mysql command interface, lol

-D = data_base = snifme
-u = mysql_user_name = ???

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> -D snifme -u mysql_user_name

You have not told me the user name you entered in the mysql command interface, lol

-D = data_base = snifme
-u = mysql_user_name = ???
oh i used my login name for ubuntu. maybe i wont do that next time XD

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> -D snifme -u mysql_user_name

You have not told me the user name you entered in the mysql command interface, lol

-D = data_base = snifme
-u = mysql_user_name = ???

well i guess its broke now, dont use your ubuntu username

---

### Post by bodhi.zazen on 2009-03-10
:lolflag:

No, IMO your mysql user and password should not be the same as actual system users.

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> :lolflag:

No, IMO your mysql user and password should not be the same as actual system users.

so is it stuck like that or could i change it to something else and how. please and thank you =)

---

### Post by bodhi.zazen on 2009-03-10
You can change it, but now you are talking mysql ...

And so you need to know what the problem is exactly b4 you can fix it and then you will need to know how to admin mysql :(

Something like this may help :

[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

To be honest I think the problem is likely you are mixing up your variables

You need to specify a data base name, user name, and password to mysql.

You can log into mysql as root and use the up arrows to review recent commands and confirm the information there.

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> You can change it, but now you are talking mysql ...

And so you need to know what the problem is exactly b4 you can fix it and then you will need to know how to admin mysql :(

Something like this may help :

[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

To be honest I think the problem is likely you are mixing up your variables

You need to specify a data base name, user name, and password to mysql.

You can log into mysql as root and use the up arrows to review recent commands and confirm the information there.

idk i figured my mysql_user_name but i get a new error ```

root@me-desktop:~# mysql -D snortsniff -u mysql_user_name -p < /usr/src/snort-2.8.3.2/schemas/create_mysql
Enter password: 
ERROR 1045 (28000): Access denied for user 'mysql_user_name'@'localhost' (using password: YES)

```

---

### Post by KEE on 2009-03-10
> **bodhi.zazen said:**
> You can change it, but now you are talking mysql ...

And so you need to know what the problem is exactly b4 you can fix it and then you will need to know how to admin mysql :(

Something like this may help :

[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

To be honest I think the problem is likely you are mixing up your variables

You need to specify a data base name, user name, and password to mysql.

You can log into mysql as root and use the up arrows to review recent commands and confirm the information there.

how do i login mysql ?

---

### Post by bodhi.zazen on 2009-03-10
Same way as before :p

```
mysql -u root -p
```

Again most likely your syntax was off , once you log in use the up arrow keys to review your previous mysql commands.

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> Same way as before :p

```
mysql -u root -p
```

Again most likely your syntax was off , once you log in use the up arrow keys to review your previous mysql commands.

ok it worked no errors =D thanks however im in another jam 
```
me@me-desktop:/var$ cd
me@me-desktop:~$ wget http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz
--2009-03-11 01:02:47--  http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 487292 (476K) [application/x-tar]
Saving to: `base-1.3.9.tar.gz.1'

100%[======================================>] 487,292     97.8K/s   in 5.2s    

2009-03-11 01:02:52 (91.9 KB/s) - `base-1.3.9.tar.gz.1' saved [487292/487292]

me@me-desktop:~$ 

```where is a good place to cd this file?

---

### Post by bodhi.zazen on 2009-03-11
Sweet. That does not matter where you save as you will extract the files and install them into /var/www/base (or what ever directory you wish). Keep following the directions on the how to ...

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> Sweet. That does not matter where you save as you will extract the files and install them into /var/www/base (or what ever directory you wish). Keep following the directions on the how to ...
ok i couldnt move it there or create the "base' folder without using nuatilus. again, also have trouble. please thank you =) 
```
me@me-desktop:~$ cd /var/www
me@me-desktop:/var/www$ cd /var/www/base
me@me-desktop:/var/www/base$ tar zvxf ~/base-1.3.9.tar.gz
tar: /home/me/base-1.3.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
me@me-desktop:/var/www/base$ /var/www/base-1.3.9.tar.gz
bash: /var/www/base-1.3.9.tar.gz: No such file or directory
me@me-desktop:/var/www/base$ cd /var/www
me@me-desktop:/var/www$ tar zvxf /var/www/base/base-1.3.9.tar.gz
base-1.3.9/
tar: base-1.3.9: Cannot mkdir: Permission denied
base-1.3.9/admin/
tar: base-1.3.9/admin: Cannot mkdir: No such file or directory
base-1.3.9/admin/base_roleadmin.php
tar: base-1.3.9/admin/base_roleadmin.php: Cannot open: No such file or directory
base-1.3.9/admin/base_useradmin.php
tar: base-1.3.9/admin/base_useradmin.php: Cannot open: No such file or directory
base-1.3.9/admin/index.php
tar: base-1.3.9/admin/index.php: Cannot open: No such file or directory
base-1.3.9/base_ag_common.php
tar: base-1.3.9/base_ag_common.php: Cannot open: No such file or directory
base-1.3.9/base_ag_main.php
tar: base-1.3.9/base_ag_main.php: Cannot open: No such file or directory
base-1.3.9/base_common.php
tar: base-1.3.9/base_common.php: Cannot open: No such file or directory
base-1.3.9/base_conf.php.dist
tar: base-1.3.9/base_conf.php.dist: Cannot open: No such file or directory
base-1.3.9/base_db_common.php
tar: base-1.3.9/base_db_common.php: Cannot open: No such file or directory
base-1.3.9/base_db_setup.php
tar: base-1.3.9/base_db_setup.php: Cannot open: No such file or directory
base-1.3.9/base_denied.php
tar: base-1.3.9/base_denied.php: Cannot open: No such file or directory
base-1.3.9/base_footer.php
tar: base-1.3.9/base_footer.php: Cannot open: No such file or directory
base-1.3.9/base_graph_common.php
tar: base-1.3.9/base_graph_common.php: Cannot open: No such file or directory
base-1.3.9/base_graph_display.php
tar: base-1.3.9/base_graph_display.php: Cannot open: No such file or directory
base-1.3.9/base_graph_form.php
tar: base-1.3.9/base_graph_form.php: Cannot open: No such file or directory
base-1.3.9/base_graph_main.php
tar: base-1.3.9/base_graph_main.php: Cannot open: No such file or directory
base-1.3.9/base_hdr1.php
tar: base-1.3.9/base_hdr1.php: Cannot open: No such file or directory
base-1.3.9/base_hdr2.php
tar: base-1.3.9/base_hdr2.php: Cannot open: No such file or directory
base-1.3.9/base_logout.php
tar: base-1.3.9/base_logout.php: Cannot open: No such file or directory
base-1.3.9/base_main.php
tar: base-1.3.9/base_main.php: Cannot open: No such file or directory
base-1.3.9/base_maintenance.php
tar: base-1.3.9/base_maintenance.php: Cannot open: No such file or directory
base-1.3.9/base_payload.php
tar: base-1.3.9/base_payload.php: Cannot open: No such file or directory
base-1.3.9/base_qry_alert.php
tar: base-1.3.9/base_qry_alert.php: Cannot open: No such file or directory
base-1.3.9/base_qry_common.php
tar: base-1.3.9/base_qry_common.php: Cannot open: No such file or directory
base-1.3.9/base_qry_form.php
tar: base-1.3.9/base_qry_form.php: Cannot open: No such file or directory
base-1.3.9/base_qry_main.php
tar: base-1.3.9/base_qry_main.php: Cannot open: No such file or directory
base-1.3.9/base_qry_sqlcalls.php
tar: base-1.3.9/base_qry_sqlcalls.php: Cannot open: No such file or directory
base-1.3.9/base_stat_alerts.php
tar: base-1.3.9/base_stat_alerts.php: Cannot open: No such file or directory
base-1.3.9/base_stat_class.php
tar: base-1.3.9/base_stat_class.php: Cannot open: No such file or directory
base-1.3.9/base_stat_common.php
tar: base-1.3.9/base_stat_common.php: Cannot open: No such file or directory
base-1.3.9/base_stat_ipaddr.php
tar: base-1.3.9/base_stat_ipaddr.php: Cannot open: No such file or directory
base-1.3.9/base_stat_iplink.php
tar: base-1.3.9/base_stat_iplink.php: Cannot open: No such file or directory
base-1.3.9/base_stat_ports.php
tar: base-1.3.9/base_stat_ports.php: Cannot open: No such file or directory
base-1.3.9/base_stat_sensor.php
tar: base-1.3.9/base_stat_sensor.php: Cannot open: No such file or directory
base-1.3.9/base_stat_time.php
tar: base-1.3.9/base_stat_time.php: Cannot open: No such file or directory
base-1.3.9/base_stat_uaddr.php
tar: base-1.3.9/base_stat_uaddr.php: Cannot open: No such file or directory
base-1.3.9/base_user.php
tar: base-1.3.9/base_user.php: Cannot open: No such file or directory
base-1.3.9/contrib/
tar: base-1.3.9/contrib: Cannot mkdir: No such file or directory
base-1.3.9/contrib/SnortUnified/
tar: base-1.3.9/contrib/SnortUnified: Cannot mkdir: No such file or directory
base-1.3.9/contrib/SnortUnified/pcaptodb.pl
tar: base-1.3.9/contrib/SnortUnified/pcaptodb.pl: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/LICENSE
tar: base-1.3.9/contrib/SnortUnified/LICENSE: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/SnortUnified/
tar: base-1.3.9/contrib/SnortUnified/SnortUnified: Cannot mkdir: No such file or directory
base-1.3.9/contrib/SnortUnified/SnortUnified/Database.pm
tar: base-1.3.9/contrib/SnortUnified/SnortUnified/Database.pm: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/SnortUnified.pm
tar: base-1.3.9/contrib/SnortUnified/SnortUnified.pm: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/uf_csv.pl
tar: base-1.3.9/contrib/SnortUnified/uf_csv.pl: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/uf_syslog.pl
tar: base-1.3.9/contrib/SnortUnified/uf_syslog.pl: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/uf_xml.pl
tar: base-1.3.9/contrib/SnortUnified/uf_xml.pl: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/ufdbtest.pl
tar: base-1.3.9/contrib/SnortUnified/ufdbtest.pl: Cannot open: No such file or directory
base-1.3.9/contrib/SnortUnified/uftester.pl
tar: base-1.3.9/contrib/SnortUnified/uftester.pl: Cannot open: No such file or directory
base-1.3.9/contrib/base-rss.php
tar: base-1.3.9/contrib/base-rss.php: Cannot open: No such file or directory
base-1.3.9/contrib/custom_base_footer.php
tar: base-1.3.9/contrib/custom_base_footer.php: Cannot open: No such file or directory
base-1.3.9/docs/
tar: base-1.3.9/docs: Cannot mkdir: No such file or directory
base-1.3.9/docs/contrib/
tar: base-1.3.9/docs/contrib: Cannot mkdir: No such file or directory
base-1.3.9/docs/contrib/CVS/
tar: base-1.3.9/docs/contrib/CVS: Cannot mkdir: No such file or directory
base-1.3.9/docs/contrib/CVS/Root
tar: base-1.3.9/docs/contrib/CVS/Root: Cannot open: No such file or directory
base-1.3.9/docs/contrib/CVS/Repository
tar: base-1.3.9/docs/contrib/CVS/Repository: Cannot open: No such file or directory
base-1.3.9/docs/contrib/CVS/Entries
tar: base-1.3.9/docs/contrib/CVS/Entries: Cannot open: No such file or directory
base-1.3.9/docs/contrib/Snort, Apache, MYSQL, PHP, and BASE instalacio&#769;n en Slackware.pdf
tar: base-1.3.9/docs/contrib/Snort, Apache, MYSQL, PHP, and BASE instalacio&#769;n en Slackware.pdf: Cannot open: No such file or directory
base-1.3.9/docs/CHANGELOG
tar: base-1.3.9/docs/CHANGELOG: Cannot open: No such file or directory
base-1.3.9/docs/CREDITS
tar: base-1.3.9/docs/CREDITS: Cannot open: No such file or directory
base-1.3.9/docs/GPL
tar: base-1.3.9/docs/GPL: Cannot open: No such file or directory
base-1.3.9/docs/README
tar: base-1.3.9/docs/README: Cannot open: No such file or directory
base-1.3.9/docs/README.mssql
tar: base-1.3.9/docs/README.mssql: Cannot open: No such file or directory
base-1.3.9/docs/TODO
tar: base-1.3.9/docs/TODO: Cannot open: No such file or directory
base-1.3.9/docs/UPGRADE
tar: base-1.3.9/docs/UPGRADE: Cannot open: No such file or directory
base-1.3.9/docs/base_faq.rtf
tar: base-1.3.9/docs/base_faq.rtf: Cannot open: No such file or directory
base-1.3.9/docs/INSTALL.rtf
tar: base-1.3.9/docs/INSTALL.rtf: Cannot open: No such file or directory
base-1.3.9/docs/INSTALL
tar: base-1.3.9/docs/INSTALL: Cannot open: No such file or directory
base-1.3.9/help/
tar: base-1.3.9/help: Cannot mkdir: No such file or directory
base-1.3.9/help/base_app_faq.php
tar: base-1.3.9/help/base_app_faq.php: Cannot open: No such file or directory
base-1.3.9/help/base_help.php
tar: base-1.3.9/help/base_help.php: Cannot open: No such file or directory
base-1.3.9/help/base_setup_help.php
tar: base-1.3.9/help/base_setup_help.php: Cannot open: No such file or directory
base-1.3.9/images/
tar: base-1.3.9/images: Cannot mkdir: No such file or directory
base-1.3.9/images/button_delete.png
tar: base-1.3.9/images/button_delete.png: Cannot open: No such file or directory
base-1.3.9/images/button_edit.png
tar: base-1.3.9/images/button_edit.png: Cannot open: No such file or directory
base-1.3.9/images/button_exclamation.png
tar: base-1.3.9/images/button_exclamation.png: Cannot open: No such file or directory
base-1.3.9/images/greencheck.gif
tar: base-1.3.9/images/greencheck.gif: Cannot open: No such file or directory
base-1.3.9/images/greencheck.png
tar: base-1.3.9/images/greencheck.png: Cannot open: No such file or directory
base-1.3.9/images/redcheck.gif
tar: base-1.3.9/images/redcheck.gif: Cannot open: No such file or directory
base-1.3.9/includes/
tar: base-1.3.9/includes: Cannot mkdir: No such file or directory
base-1.3.9/includes/base_action.inc.php
tar: base-1.3.9/includes/base_action.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_auth.inc.php
tar: base-1.3.9/includes/base_auth.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_cache.inc.php
tar: base-1.3.9/includes/base_cache.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_capabilities.php
tar: base-1.3.9/includes/base_capabilities.php: Cannot open: No such file or directory
base-1.3.9/includes/base_constants.inc.php
tar: base-1.3.9/includes/base_constants.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_db.inc.php
tar: base-1.3.9/includes/base_db.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_include.inc.php
tar: base-1.3.9/includes/base_include.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_log_error.inc.php
tar: base-1.3.9/includes/base_log_error.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_log_timing.inc.php
tar: base-1.3.9/includes/base_log_timing.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_net.inc.php
tar: base-1.3.9/includes/base_net.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_output_html.inc.php
tar: base-1.3.9/includes/base_output_html.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_output_query.inc.php
tar: base-1.3.9/includes/base_output_query.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_setup.inc.php
tar: base-1.3.9/includes/base_setup.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_signature.inc.php
tar: base-1.3.9/includes/base_signature.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_state_citems.inc.php
tar: base-1.3.9/includes/base_state_citems.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_state_common.inc.php
tar: base-1.3.9/includes/base_state_common.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_state_criteria.inc.php
tar: base-1.3.9/includes/base_state_criteria.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_state_query.inc.php
tar: base-1.3.9/includes/base_state_query.inc.php: Cannot open: No such file or directory
base-1.3.9/includes/base_template.php
tar: base-1.3.9/includes/base_template.php: Cannot open: No such file or directory
base-1.3.9/includes/base_user.inc.php
tar: base-1.3.9/includes/base_user.inc.php: Cannot open: No such file or directory
base-1.3.9/index.php
tar: base-1.3.9/index.php: Cannot open: No such file or directory
base-1.3.9/languages/
tar: base-1.3.9/languages: Cannot mkdir: No such file or directory
base-1.3.9/languages/chinese.lang.php
tar: base-1.3.9/languages/chinese.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/czech.lang.php
tar: base-1.3.9/languages/czech.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/danish.lang.php
tar: base-1.3.9/languages/danish.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/english.lang.php
tar: base-1.3.9/languages/english.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/finnish.lang.php
tar: base-1.3.9/languages/finnish.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/french.lang.php
tar: base-1.3.9/languages/french.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/german.lang.php
tar: base-1.3.9/languages/german.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/index.php
tar: base-1.3.9/languages/index.php: Cannot open: No such file or directory
base-1.3.9/languages/indonesian.lang.php
tar: base-1.3.9/languages/indonesian.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/italian.lang.php
tar: base-1.3.9/languages/italian.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/japanese.lang.php
tar: base-1.3.9/languages/japanese.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/norwegian.lang.php
tar: base-1.3.9/languages/norwegian.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/polish.lang.php
tar: base-1.3.9/languages/polish.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/portuguese-PT.lang.php
tar: base-1.3.9/languages/portuguese-PT.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/portuguese.lang.php
tar: base-1.3.9/languages/portuguese.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/russian.lang.php
tar: base-1.3.9/languages/russian.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/simplified_chinese.lang.php
tar: base-1.3.9/languages/simplified_chinese.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/spanish.lang.php
tar: base-1.3.9/languages/spanish.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/swedish.lang.php
tar: base-1.3.9/languages/swedish.lang.php: Cannot open: No such file or directory
base-1.3.9/languages/turkish.lang.php
tar: base-1.3.9/languages/turkish.lang.php: Cannot open: No such file or directory
base-1.3.9/scripts/
tar: base-1.3.9/scripts: Cannot mkdir: No such file or directory
base-1.3.9/scripts/base_maintenance.pl
tar: base-1.3.9/scripts/base_maintenance.pl: Cannot open: No such file or directory
base-1.3.9/setup/
tar: base-1.3.9/setup: Cannot mkdir: No such file or directory
base-1.3.9/setup/base_conf_contents.php
tar: base-1.3.9/setup/base_conf_contents.php: Cannot open: No such file or directory
base-1.3.9/setup/index.php
tar: base-1.3.9/setup/index.php: Cannot open: No such file or directory
base-1.3.9/setup/setup1.php
tar: base-1.3.9/setup/setup1.php: Cannot open: No such file or directory
base-1.3.9/setup/setup2.php
tar: base-1.3.9/setup/setup2.php: Cannot open: No such file or directory
base-1.3.9/setup/setup3.php
tar: base-1.3.9/setup/setup3.php: Cannot open: No such file or directory
base-1.3.9/setup/setup4.php
tar: base-1.3.9/setup/setup4.php: Cannot open: No such file or directory
base-1.3.9/setup/setup5.php
tar: base-1.3.9/setup/setup5.php: Cannot open: No such file or directory
base-1.3.9/setup/setup_db.inc.php
tar: base-1.3.9/setup/setup_db.inc.php: Cannot open: No such file or directory
base-1.3.9/sql/
tar: base-1.3.9/sql: Cannot mkdir: No such file or directory
base-1.3.9/sql/acid2base_tbls_mssql.sql
tar: base-1.3.9/sql/acid2base_tbls_mssql.sql: Cannot open: No such file or directory
base-1.3.9/sql/acid2base_tbls_mysql.sql
tar: base-1.3.9/sql/acid2base_tbls_mysql.sql: Cannot open: No such file or directory
base-1.3.9/sql/acid2base_tbls_pgsql.sql
tar: base-1.3.9/sql/acid2base_tbls_pgsql.sql: Cannot open: No such file or directory
base-1.3.9/sql/create_base_tbls_mssql.sql
tar: base-1.3.9/sql/create_base_tbls_mssql.sql: Cannot open: No such file or directory
base-1.3.9/sql/create_base_tbls_mssql_extra.sql
tar: base-1.3.9/sql/create_base_tbls_mssql_extra.sql: Cannot open: No such file or directory
base-1.3.9/sql/create_base_tbls_mysql.sql
tar: base-1.3.9/sql/create_base_tbls_mysql.sql: Cannot open: No such file or directory
base-1.3.9/sql/create_base_tbls_oracle.sql
tar: base-1.3.9/sql/create_base_tbls_oracle.sql: Cannot open: No such file or directory
base-1.3.9/sql/create_base_tbls_pgsql.sql
tar: base-1.3.9/sql/create_base_tbls_pgsql.sql: Cannot open: No such file or directory
base-1.3.9/sql/create_base_tbls_pgsql_extra.sql
tar: base-1.3.9/sql/create_base_tbls_pgsql_extra.sql: Cannot open: No such file or directory
base-1.3.9/sql/upgrade_0.9.x_to_1.0-mysql.sql
tar: base-1.3.9/sql/upgrade_0.9.x_to_1.0-mysql.sql: Cannot open: No such file or directory
base-1.3.9/styles/
tar: base-1.3.9/styles: Cannot mkdir: No such file or directory
base-1.3.9/styles/acid_style.css
tar: base-1.3.9/styles/acid_style.css: Cannot open: No such file or directory
base-1.3.9/styles/base_black_style.css
tar: base-1.3.9/styles/base_black_style.css: Cannot open: No such file or directory
base-1.3.9/styles/base_red_style.css
tar: base-1.3.9/styles/base_red_style.css: Cannot open: No such file or directory
base-1.3.9/styles/base_style.css
tar: base-1.3.9/styles/base_style.css: Cannot open: No such file or directory
tar: Error exit delayed from previous errors

```

---

### Post by bodhi.zazen on 2009-03-11
It appears you forgot to use sudo ...

sudo tar ....

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> It appears you forgot to use sudo ...

sudo tar ....
oh k, thanks =D oh am I cd'ing the tar.gz or the base-1.3.9 extracted folder itself? jus wanna know before i continue to make sure. thanks a lot =D

---

### Post by bodhi.zazen on 2009-03-11
cd ?

I would 

cd /var/www
sudo tar zvxf /var/www/base/base-1.3.9.tar.gz

Then ls (so you can see what is in /var/www). You are going to need to keep straight where the "base" directory is for Apache as what is the base .tar :twisted:

---

### Post by KEE on 2009-03-11
ok it worked  =) but ...```
me@me-desktop:/var/www/base/base$ cp -R /usr/src/snort-2.8.3.2/doc/singatures .
cp: cannot stat `/usr/src/snort-2.8.3.2/doc/singatures': No such file or directory
me@me-desktop:/var/www/base/base$ 
```and theres no file there under "singatures" please help and thanks =)

---

### Post by bodhi.zazen on 2009-03-11
You can skip that step.

It depends on which set of snort rules you downloaded, there are no signatures if you did not register with snort.

The signatures are a set of text files you can place on your local box to get an explanation of rules if there is an alert.

Each alert, however, comes with several links to the same information on several web sites (for cross reference) so you do not really *need* them on your local box ;)

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> You can skip that step.

It depends on which set of snort rules you downloaded, there are no signatures if you did not register with snort.

The signatures are a set of text files you can place on your local box to get an explanation of rules if there is an alert.

Each alert, however, comes with several links to the same information on several web sites (for cross reference) so you do not really *need* them on your local box ;)

alright, do i skip any sequence after that? or they separate tasks?   ```
cp -R /usr/src/snort-2.8.3/doc/signatures .
cd ..
chown -R www-data.www-data base
```and then move on to ```
pear install Image_Color Image_Canvas-alpha Image_Graph-alpha
```

---

### Post by bodhi.zazen on 2009-03-11
Just skip that single step

Also take care with that "cd ..", make sure you in in the proper directory ;)

And when you are done we want to see a screen shot of base in Firefox (or whatever browser you use) :twisted:

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> Just skip that single step

Also take care with that "cd ..", make sure you in in the proper directory ;)

And when you are done we want to see a screen shot of base in Firefox (or whatever browser you use) :twisted:

oh so is this right?```
cd /var/www/base/base
```

---

### Post by bodhi.zazen on 2009-03-11
Not sure, you will have to look at the contents of what is where ;)

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> Not sure, you will have to look at the contents of what is where ;)

oh alright well everything moved form base-1.3.9 to just base or the directory changed to just /var/www/base/base instead of /var/www/base/base-1.3.9. also, command line is in since you told me to skip that last command. ```
me@me-desktop:/var/www/base/base$ 

```

---

### Post by bodhi.zazen on 2009-03-11
IMO you should move everything from /var/www/base/base

to just /var/www/base

then cd /var/www

and continue with 

"sudo chown -R www-data.www-data base"

(do not forget to use sudo ;) )

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> IMO you should move everything from /var/www/base/base

to just /var/www/base

then cd /var/www

and continue with 

"sudo chown -R www-data.www-data base"

(do not forget to use sudo ;) )o alright then something happen here =/ i shouldnt have moved it, but i think thats was me using nautilus again =P i was trying to get a command to work or i most did ```
sudo mv base-1.3.9 base
``````
me@me-desktop:/var/www/base$ mv base-1.3.9 base
mv: cannot move `base-1.3.9' to `base': 
Permission denied
me@me-desktop:/var/www/base$ sudo mv base-1.3.9 base
me@me-desktop:/var/www/base$ cd base
me@me-desktop:/var/www/base/base$ sudo cd base
sudo: cd: command not found
me@me-desktop:/var/www/base/base$ cp -R /usr/src/snort-2.8.3.2/doc/singatures .
cp: cannot stat `/usr/src/snort-2.8.3.2/doc/singatures': No such file or directory
me@me-desktop:/var/www/base/base$ 

```

---

### Post by Vantrax on 2009-03-11
After seeing that last post I think you may get some benefit from here: [http://gd.tuwien.ac.at/linuxcommand.org/index.php](http://gd.tuwien.ac.at/linuxcommand.org/index.php)

It appears that you are not quite comfortable with using the terminal yet.

---

### Post by bodhi.zazen on 2009-03-11
You will have to look at the contents of the directories.

Move everything from /var/www/base/base to /var/www/base

Then delete the (now empty) /var/www/base/base

---

### Post by KEE on 2009-03-11
> **Vantrax said:**
> After seeing that last post I think you may get some benefit from here: [http://gd.tuwien.ac.at/linuxcommand.org/index.php](http://gd.tuwien.ac.at/linuxcommand.org/index.php)

It appears that you are not quite comfortable with using the terminal yet.

o ok, thanks. however im just copying the codes and pasting =/  anyway heres what went wrong. codes from [http://ubuntuforums.org/showpost.php?p=5786356&postcount=4](http://ubuntuforums.org/showpost.php?p=5786356&postcount=4)```
me@me-desktop:/var/www/base$ cd /var/www/base
me@me-desktop:/var/www/base$ sudo tar zvxf /var/www/base/base-1.3.9.tar.gz
[sudo] password for me: 
base-1.3.9/
base-1.3.9/admin/
base-1.3.9/admin/base_roleadmin.php
base-1.3.9/admin/base_useradmin.php
base-1.3.9/admin/index.php
base-1.3.9/base_ag_common.php
base-1.3.9/base_ag_main.php
base-1.3.9/base_common.php
base-1.3.9/base_conf.php.dist
base-1.3.9/base_db_common.php
base-1.3.9/base_db_setup.php
base-1.3.9/base_denied.php
base-1.3.9/base_footer.php
base-1.3.9/base_graph_common.php
base-1.3.9/base_graph_display.php
base-1.3.9/base_graph_form.php
base-1.3.9/base_graph_main.php
base-1.3.9/base_hdr1.php
base-1.3.9/base_hdr2.php
base-1.3.9/base_logout.php
base-1.3.9/base_main.php
base-1.3.9/base_maintenance.php
base-1.3.9/base_payload.php
base-1.3.9/base_qry_alert.php
base-1.3.9/base_qry_common.php
base-1.3.9/base_qry_form.php
base-1.3.9/base_qry_main.php
base-1.3.9/base_qry_sqlcalls.php
base-1.3.9/base_stat_alerts.php
base-1.3.9/base_stat_class.php
base-1.3.9/base_stat_common.php
base-1.3.9/base_stat_ipaddr.php
base-1.3.9/base_stat_iplink.php
base-1.3.9/base_stat_ports.php
base-1.3.9/base_stat_sensor.php
base-1.3.9/base_stat_time.php
base-1.3.9/base_stat_uaddr.php
base-1.3.9/base_user.php
base-1.3.9/contrib/
base-1.3.9/contrib/SnortUnified/
base-1.3.9/contrib/SnortUnified/pcaptodb.pl
base-1.3.9/contrib/SnortUnified/LICENSE
base-1.3.9/contrib/SnortUnified/SnortUnified/
base-1.3.9/contrib/SnortUnified/SnortUnified/Database.pm
base-1.3.9/contrib/SnortUnified/SnortUnified.pm
base-1.3.9/contrib/SnortUnified/uf_csv.pl
base-1.3.9/contrib/SnortUnified/uf_syslog.pl
base-1.3.9/contrib/SnortUnified/uf_xml.pl
base-1.3.9/contrib/SnortUnified/ufdbtest.pl
base-1.3.9/contrib/SnortUnified/uftester.pl
base-1.3.9/contrib/base-rss.php
base-1.3.9/contrib/custom_base_footer.php
base-1.3.9/docs/
base-1.3.9/docs/contrib/
base-1.3.9/docs/contrib/CVS/
base-1.3.9/docs/contrib/CVS/Root
base-1.3.9/docs/contrib/CVS/Repository
base-1.3.9/docs/contrib/CVS/Entries
base-1.3.9/docs/contrib/Snort, Apache, MYSQL, PHP, and BASE instalacio&#769;n en Slackware.pdf
base-1.3.9/docs/CHANGELOG
base-1.3.9/docs/CREDITS
base-1.3.9/docs/GPL
base-1.3.9/docs/README
base-1.3.9/docs/README.mssql
base-1.3.9/docs/TODO
base-1.3.9/docs/UPGRADE
base-1.3.9/docs/base_faq.rtf
base-1.3.9/docs/INSTALL.rtf
base-1.3.9/docs/INSTALL
base-1.3.9/help/
base-1.3.9/help/base_app_faq.php
base-1.3.9/help/base_help.php
base-1.3.9/help/base_setup_help.php
base-1.3.9/images/
base-1.3.9/images/button_delete.png
base-1.3.9/images/button_edit.png
base-1.3.9/images/button_exclamation.png
base-1.3.9/images/greencheck.gif
base-1.3.9/images/greencheck.png
base-1.3.9/images/redcheck.gif
base-1.3.9/includes/
base-1.3.9/includes/base_action.inc.php
base-1.3.9/includes/base_auth.inc.php
base-1.3.9/includes/base_cache.inc.php
base-1.3.9/includes/base_capabilities.php
base-1.3.9/includes/base_constants.inc.php
base-1.3.9/includes/base_db.inc.php
base-1.3.9/includes/base_include.inc.php
base-1.3.9/includes/base_log_error.inc.php
base-1.3.9/includes/base_log_timing.inc.php
base-1.3.9/includes/base_net.inc.php
base-1.3.9/includes/base_output_html.inc.php
base-1.3.9/includes/base_output_query.inc.php
base-1.3.9/includes/base_setup.inc.php
base-1.3.9/includes/base_signature.inc.php
base-1.3.9/includes/base_state_citems.inc.php
base-1.3.9/includes/base_state_common.inc.php
base-1.3.9/includes/base_state_criteria.inc.php
base-1.3.9/includes/base_state_query.inc.php
base-1.3.9/includes/base_template.php
base-1.3.9/includes/base_user.inc.php
base-1.3.9/index.php
base-1.3.9/languages/
base-1.3.9/languages/chinese.lang.php
base-1.3.9/languages/czech.lang.php
base-1.3.9/languages/danish.lang.php
base-1.3.9/languages/english.lang.php
base-1.3.9/languages/finnish.lang.php
base-1.3.9/languages/french.lang.php
base-1.3.9/languages/german.lang.php
base-1.3.9/languages/index.php
base-1.3.9/languages/indonesian.lang.php
base-1.3.9/languages/italian.lang.php
base-1.3.9/languages/japanese.lang.php
base-1.3.9/languages/norwegian.lang.php
base-1.3.9/languages/polish.lang.php
base-1.3.9/languages/portuguese-PT.lang.php
base-1.3.9/languages/portuguese.lang.php
base-1.3.9/languages/russian.lang.php
base-1.3.9/languages/simplified_chinese.lang.php
base-1.3.9/languages/spanish.lang.php
base-1.3.9/languages/swedish.lang.php
base-1.3.9/languages/turkish.lang.php
base-1.3.9/scripts/
base-1.3.9/scripts/base_maintenance.pl
base-1.3.9/setup/
base-1.3.9/setup/base_conf_contents.php
base-1.3.9/setup/index.php
base-1.3.9/setup/setup1.php
base-1.3.9/setup/setup2.php
base-1.3.9/setup/setup3.php
base-1.3.9/setup/setup4.php
base-1.3.9/setup/setup5.php
base-1.3.9/setup/setup_db.inc.php
base-1.3.9/sql/
base-1.3.9/sql/acid2base_tbls_mssql.sql
base-1.3.9/sql/acid2base_tbls_mysql.sql
base-1.3.9/sql/acid2base_tbls_pgsql.sql
base-1.3.9/sql/create_base_tbls_mssql.sql
base-1.3.9/sql/create_base_tbls_mssql_extra.sql
base-1.3.9/sql/create_base_tbls_mysql.sql
base-1.3.9/sql/create_base_tbls_oracle.sql
base-1.3.9/sql/create_base_tbls_pgsql.sql
base-1.3.9/sql/create_base_tbls_pgsql_extra.sql
base-1.3.9/sql/upgrade_0.9.x_to_1.0-mysql.sql
base-1.3.9/styles/
base-1.3.9/styles/acid_style.css
base-1.3.9/styles/base_black_style.css
base-1.3.9/styles/base_red_style.css
base-1.3.9/styles/base_style.css
me@me-desktop:/var/www/base$ mv base-1.3.9 base
mv: cannot move `base-1.3.9' to `base': Permission denied
me@me-desktop:/var/www/base$ sudo mv base-1.3.9 base
me@me-desktop:/var/www/base$ cd base
me@me-desktop:/var/www/base/base$ sudo cd base
sudo: cd: command not found
me@me-desktop:/var/www/base/base$ cp -R /usr/src/snort-2.8.3.2/doc/singatures .
cp: cannot stat `/usr/src/snort-2.8.3.2/doc/singatures': No such file or directory
me@me-desktop:/var/www/base/base$ sudo mv base to www
[sudo] password for me: 
mv: target `www' is not a directory
me@me-desktop:/var/www/base/base$ /var/www/base
bash: /var/www/base: is a directory
me@me-desktop:/var/www/base/base$ cd base
bash: cd: base: No such file or directory
me@me-desktop:/var/www/base/base$ 
```

---

### Post by bodhi.zazen on 2009-03-11
We understand what you did, but it hard to follow as you have everything in /var/www/base/base rather then /var/www/base (which is simpler) and you have mis-typed some command and what now.

So at this point I do not know what in in /var/www/base and what is in /var/www/base/base

so ..

```
cd /var/www/base/base
sudo cp -R ./* ..
cd /var/www/base
sudo rm -rf base
```Then continue with the tutorial at 

sudo chown www-data.www-data base 

and on ...

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> We understand what you did, but it hard to follow as you have everything in /var/www/base/base rather then /var/www/base (which is simpler) and you have mis-typed some command and what now.

So at this point I do not know what in in /var/www/base and what is in /var/www/base/base

so ..

```
cd /var/www/base/base
sudo cp -R ./* ..
cd /var/www/base
sudo rm -rf base
```Then continue with the tutorial at 

sudo chown www-data.www-data base 

and on ...ok that work and i checked to see if everything got moved and it did. i cant get that command to though```
me@me-desktop:/var/www/base$ cd /var/www/base
me@me-desktop:/var/www/base$ sudo chown www-data.www-data base 
chown: cannot access `base': No such file or directory
me@me-desktop:/var/www/base$ cd base
bash: cd: base: No such file or directory
me@me-desktop:/var/www/base$ 
```

---

### Post by bodhi.zazen on 2009-03-11
cd /var/www

chown **-R** www-data.www-data base

...

---

### Post by KEE on 2009-03-11
> **bodhi.zazen said:**
> cd /var/www

chown **-R** www-data.www-data base

...hmm 

```
me@me-desktop:~$ cd /var/www
me@me-desktop:/var/www$ sudo chown -R www-data.www base
chown: invalid user: `www-data.www'
```
do you mean ```
sudo -i
```

---

### Post by KEE on 2009-03-12
no luck figuring this out on my own. i was thinking that data could be "database" but no. anyway, need help please thank you =)

---

### Post by dannyboy79 on 2009-03-12
> **KEE said:**
> hmm 

```
me@me-desktop:~$ cd /var/www
me@me-desktop:/var/www$ sudo chown -R www-data.www base
chown: invalid user: `www-data.www'
```
do you mean ```
sudo -i
```

if you're copying and pasting the commands from here then you wouldn't have gotten this error.

Note, his command was this:
```
chown -R www-data.www-data base
```

whereas you typed in:
```
sudo chown -R www-data.www base
```

you're missing the second -data after .www. It can get very time consuming for people when they try to help you if you don't do what they are informing you to do. Just my 2 cents.

---

### Post by bodhi.zazen on 2009-03-12
Sorry, my mistake

sudo chown -R www-data.www-data base

---

### Post by KEE on 2009-03-12
> **bodhi.zazen said:**
> Sorry, my mistake

sudo chown -R www-data.www-data base

no biggy, your great at helping =D hmm i get this error in the next line =)```
me@me-desktop:/var/www$ pear install Image_Color Image_Canvas-alpha Image_Graph-alpha
WARNING: channel "pear.php.net" has updated its protocols, use "channel-update pear.php.net" to update
Cannot install, php_dir for channel "pear.php.net" is not writeable by the current user
me@me-desktop:/var/www$ 


```has that changed to this ?```
channel-update pear.php.net install Image_Color Image_Canvas-alpha Image_Graph-alpha
```

---

### Post by Vantrax on 2009-03-12
Kee you should really look through that terminal commands link I posted.

It makes it difficult for people to help you when you do not understand how to use a terminal, or what commands represent.

---

### Post by KEE on 2009-03-12
> **Vantrax said:**
> Kee you should really look through that terminal commands link I posted.

It makes it difficult for people to help you when you do not understand how to use a terminal, or what commands represent.

Ook so what do search for at [http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php) so that I may know it =D  some commands found there dont work at all =/ i tried some previously but it just gives me errors. anyway still need help =) please and thank you

---

### Post by bodhi.zazen on 2009-03-12
All or most of the command need to be entered as root.

So either use sudo <command>

Or become root with

```
sudo -i
```

---

### Post by KEE on 2009-03-12
> **bodhi.zazen said:**
> All or most of the command need to be entered as root.

So either use sudo <command>

Or become root with

```
sudo -i
```

oh right right. i forgot to do that again since i restarted. thanks so much =)

---

### Post by KEE on 2009-03-12
ok how do you save the doc? i wrote ```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

``` at the buttom of the doc in terminal but im not sure how to save. thanks so much for help =D

---

### Post by bodhi.zazen on 2009-03-12
First I hope you opened the document with sudo nano ....

In that case, hit Ctrl-X , type y to save :)

If not what command did you use ?

---

### Post by KEE on 2009-03-12
> **bodhi.zazen said:**
> First I hope you opened the document with sudo nano ....

In that case, hit Ctrl-X , type y to save :)

If not what command did you use ?

hmm not sure, i cannot scroll up, but i was in root when i did it, and the doc showed up with no errors that i know of or anything ill just show where  i placed the text in the doc```
GNU nano 2.0.7                                                   File: /etc/apache2/apache2.conf                                                                                                   Modified  

# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml


```

---

### Post by bodhi.zazen on 2009-03-12
That is nano, but you will not be able to save your changes if you did not start it as root.

sudo nano/etc/apache2/apache2.conf

:twisted:

---

### Post by KEE on 2009-03-12
> **bodhi.zazen said:**
> That is nano, but you will not be able to save your changes if you did not start it as root.

sudo nano/etc/apache2/apache2.conf

:twisted:

k, thats done. thanks, hmm 127.0.1.1 thats not going anywhere but just my computer. what to do here? ```
root@me-desktop:~# sudo nano /etc/apache2/apache2.conf
root@me-desktop:~# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting .apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@me-desktop:~# 

```

---

### Post by bodhi.zazen on 2009-03-12
That is a common error :

[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache)

Then re-start apache.

then open firefox and go to :

[http://localhost/base](http://localhost/base)

---

### Post by KEE on 2009-03-12
> **bodhi.zazen said:**
> That is a common error :

[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache)

Then re-start apache.

then open firefox and go to :

[http://localhost/base](http://localhost/base)

what is that link? its asking to save something?

---

### Post by KEE on 2009-03-12
O ok its Basic Analysis and Security Engine (BASE) doc.phtml.part. what do i do with that =D

---

### Post by bodhi.zazen on 2009-03-12
Follow steps 1-5 near the bottom of post #4 of this thread :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Basically you need to put in some information, including your mysql database, user, and username (remember these are NOT the same as your log in name and password, you entered this information when you installed and configured mysql).

---

### Post by KEE on 2009-03-12
> **bodhi.zazen said:**
> Follow steps 1-5 near the bottom of post #4 of this thread :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Basically you need to put in some information, including your mysql database, user, and username (remember these are NOT the same as your log in name and password, you entered this information when you installed and configured mysql).ok, i dont understand something. this is what i got from that link ```
<?php
/*******************************************************************************
** Basic Analysis and Security Engine (BASE)
** Copyright (C) 2004 BASE Project Team
** Copyright (C) 2000 Carnegie Mellon University
**
** (see the file 'base_main.php' for license details)
**
** Project Leads: Kevin Johnson <kjohnson@secureideas.net>
**                Sean Muller <samwise_diver@users.sourceforge.net>
** Built upon work by Roman Danyliw <rdd@cert.org>, <roman@danyliw.com>
**
** Purpose: Determines if a login is needed.  If not, will redirect you
**  to base_main.php
********************************************************************************
** Authors:
********************************************************************************
** Kevin Johnson <kjohnson@secureideas.net
**
********************************************************************************
*/

/**
 *  Check to see if the base_conf.php file exists and is big enough...
 *  if not redirect to the setup/index.php page
*/
if (!file_exists('base_conf.php') || filesize('base_conf.php') < 10) {
    header( 'Location: setup/index.php' );
    die();
    }

require("base_conf.php");
include("$BASE_path/includes/base_include.inc.php");
include_once("$BASE_path/base_db_common.php");

$errorMsg      = "";
$displayError  = 0;
$noDisplayMenu = 1;

// Redirect to base_main.php if auth system is off
if ( $Use_Auth_System == 0 ) {
    base_header("Location: base_main.php");
}

if (isset($_POST['submit'])) {
    $debug_mode = 0; // wont login with debug_mode
    $BASEUSER   = new BaseUser();
    $user       = filterSql($_POST['login']);
    $pwd        = filterSql($_POST['password']);

    if (($BASEUSER->Authenticate($user, $pwd)) == 0) {
        header("Location: base_main.php");
	exit();
    }
} else {
    $displayError = 1;
    $errorMsg     = _LOGINERROR;
}
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<!-- <?php echo _TITLE . $BASE_VERSION; ?> -->
<html>

<head>
  <meta http-equiv="Content-Type" content="text/html; charset=<?php echo(_CHARSET); ?>" />
  <meta http-equiv="pragma" content="no-cache" />
  <title><?php echo(_TITLE . $BASE_VERSION); ?></title>
  <link rel="stylesheet" type="text/css" href="styles/<?php echo($base_style); ?>" />
</head>
<body onload="javascript:document.loginform.login.focus();">
  <div class="mainheadertitle">&nbsp;
<?php echo _TITLE; ?>
  </div><br />
<?php
if ($displayError == 1)
{
    echo "<div class='errorMsg' align='center'>$errorMsg</div>";
}
?>
<form action="index.php" method="post" name="loginform">
  <table width="75%" style='border:0;padding:0;margin:auto;'>
    <tr>
      <td align="right" width="50%"><?php echo _FRMLOGIN; ?>&nbsp;</td>
      <td align="left" width="50%"><input type="text" name="login"></td>
    </tr>
    <tr>
      <td align="right"><?php echo _FRMPWD; ?>&nbsp;</td>
      <td align="left"><input type="password" name="password" /></td>
    </tr>
    <tr>
      <td colspan="2" align="center">
        <input type="submit" name="submit" value="Login" />
        <input type="reset" name="reset" />
      </td>
    </tr>
  </table>
</form>
<?php
  include("$BASE_path/base_footer.php");
?>
</body>
</html
```where do i start the steps?

---

### Post by KEE on 2009-03-12
oh i get it you have to open it up with firefox =) hmm is this right ?```
** Sean Muller ** Built upon work by Roman Danyliw , ** ** Purpose: Determines if a login is needed. If not, will redirect you ** to base_main.php ******************************************************************************** ** Authors: ******************************************************************************** ** Kevin Johnson < 10) { header( 'Location: setup/index.php' ); die(); } require("base_conf.php"); include("$BASE_path/includes/base_include.inc.php"); include_once("$BASE_path/base_db_common.php"); $errorMsg = ""; $displayError = 0; $noDisplayMenu = 1; // Redirect to base_main.php if auth system is off if ( $Use_Auth_System == 0 ) { base_header("Location: base_main.php"); } if (isset($_POST['submit'])) { $debug_mode = 0; // wont login with debug_mode $BASEUSER = new BaseUser(); $user = filterSql($_POST['login']); $pwd = filterSql($_POST['password']); if (($BASEUSER->Authenticate($user, $pwd)) == 0) { header("Location: base_main.php"); exit(); } } else { $displayError = 1; $errorMsg = _LOGINERROR; } ?>
 

$errorMsg"; } ?> 
``` then its asking for login name and password ?

---

### Post by bodhi.zazen on 2009-03-13
You need to now configure apache to use php (it is a pain ;)

See my post here : [http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by KEE on 2009-03-13
> **bodhi.zazen said:**
> You need to now configure apache to use php (it is a pain ;)

See my post here : [http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

ive used apache with netframwork on winxp before  =) some commands don't work. could i skip php4?  ```
root@me-desktop:~# sudo apt-get install libapache2-mod-php4 php4-cli php4-common php4-cgi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-php4 has no installation candidate
root@me-desktop:~# 

```

---

### Post by bodhi.zazen on 2009-03-13
Well, no you will need php.

Personally I use php5.

See the first post in this thread :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Under step 1. prep I have an apt-get command to install everything I needed, including php5.

---

### Post by KEE on 2009-03-13
> **bodhi.zazen said:**
> Well, no you will need php.

Personally I use php5.

See the first post in this thread :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Under step 1. prep I have an apt-get command to install everything I needed, including php5.

wow the mod for php5 took a long time =/ i am at the part where i edit /etc/apache2/apache2.conf file. were do i put DirectoryIndex index.html index.cgi index.pl index.php index.xhtml?

---

### Post by bodhi.zazen on 2009-03-14
You can put it at the bottom of the file.

---

### Post by KEE on 2009-03-14
> **bodhi.zazen said:**
> You can put it at the bottom of the file.

wow this is hard !! what im i doing wrong ?```

# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```

and still get this at the top ```
** Sean Muller ** Built upon work by Roman Danyliw , ** ** Purpose: Determines if a login is needed. If not, will redirect you ** to base_main.php ******************************************************************************** ** Authors: ******************************************************************************** ** Kevin Johnson < 10) { header( 'Location: setup/index.php' ); die(); } require("base_conf.php"); include("$BASE_path/includes/base_include.inc.php"); include_once("$BASE_path/base_db_common.php"); $errorMsg = ""; $displayError = 0; $noDisplayMenu = 1; // Redirect to base_main.php if auth system is off if ( $Use_Auth_System == 0 ) { base_header("Location: base_main.php"); } if (isset($_POST['submit'])) { $debug_mode = 0; // wont login with debug_mode $BASEUSER = new BaseUser(); $user = filterSql($_POST['login']); $pwd = filterSql($_POST['password']); if (($BASEUSER->Authenticate($user, $pwd)) == 0) { header("Location: base_main.php"); exit(); } } else { $displayError = 1; $errorMsg = _LOGINERROR; } ?>
 

$errorMsg"; } ?> 
```

---

### Post by bodhi.zazen on 2009-03-14
you need to re-start apache after making that edit, then re-start firefox.

---

### Post by KEE on 2009-03-14
> **bodhi.zazen said:**
> you need to re-start apache after making that edit, then re-start firefox.
this mean anything? i get that same text in in the browser as before, check out what i get in terminal. any ideas?
```

me@me-desktop:~$ sudo  sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
me@me-desktop:~$ sudo firefox restart
Segmentation fault
me@me-desktop:~$ 

```

---

### Post by bodhi.zazen on 2009-03-15
LOL

close firefox ...

then re-open firefox and enter :

[http://localhost/base](http://localhost/base)

---

### Post by KEE on 2009-03-15
same login screen with weird text```
** Sean Muller ** Built upon work by Roman Danyliw , ** ** Purpose: Determines if a login is needed. If not, will redirect you ** to base_main.php ******************************************************************************** ** Authors: ******************************************************************************** ** Kevin Johnson < 10) { header( 'Location: setup/index.php' ); die(); } require("base_conf.php"); include("$BASE_path/includes/base_include.inc.php"); include_once("$BASE_path/base_db_common.php"); $errorMsg = ""; $displayError = 0; $noDisplayMenu = 1; // Redirect to base_main.php if auth system is off if ( $Use_Auth_System == 0 ) { base_header("Location: base_main.php"); } if (isset($_POST['submit'])) { $debug_mode = 0; // wont login with debug_mode $BASEUSER = new BaseUser(); $user = filterSql($_POST['login']); $pwd = filterSql($_POST['password']); if (($BASEUSER->Authenticate($user, $pwd)) == 0) { header("Location: base_main.php"); exit(); } } else { $displayError = 1; $errorMsg = _LOGINERROR; } ?>
 

$errorMsg"; } ?> 
```
also my browser changed  to like netscape or somethin aswell has a new ALT+HOME. new home is [http://www.restart.com/](http://www.restart.com/)

---

### Post by KEE on 2009-03-17
please help and thank you =)

---

### Post by bodhi.zazen on 2009-03-17
Your apache installation is not displaying the php properly.

did you make the edit ?

did you re-start apache ?

did you restart your browser (close and re-start firefox ?)

did you clear your (firefox) cache ?

---

### Post by KEE on 2009-03-17
> **bodhi.zazen said:**
> Your apache installation is not displaying the php properly.

did you make the edit ?

did you re-start apache ?

did you restart your browser (close and re-start firefox ?)

did you clear your (firefox) cache ?ok I did 3 out of 4. how do you clear your firefox cache? i couldnt find the folder under firefox/cache when i did the search

---

### Post by bodhi.zazen on 2009-03-17
Tools -> clear private data.

---

### Post by KEE on 2009-03-17
ok i did clear the cache =) but i still get this ```
** Sean Muller ** Built upon work by Roman Danyliw , ** ** Purpose: Determines if a login is needed. If not, will redirect you ** to base_main.php ******************************************************************************** ** Authors: ******************************************************************************** ** Kevin Johnson < 10) { header( 'Location: setup/index.php' ); die(); } require("base_conf.php"); include("$BASE_path/includes/base_include.inc.php"); include_once("$BASE_path/base_db_common.php"); $errorMsg = ""; $displayError = 0; $noDisplayMenu = 1; // Redirect to base_main.php if auth system is off if ( $Use_Auth_System == 0 ) { base_header("Location: base_main.php"); } if (isset($_POST['submit'])) { $debug_mode = 0; // wont login with debug_mode $BASEUSER = new BaseUser(); $user = filterSql($_POST['login']); $pwd = filterSql($_POST['password']); if (($BASEUSER->Authenticate($user, $pwd)) == 0) { header("Location: base_main.php"); exit(); } } else { $displayError = 1; $errorMsg = _LOGINERROR; } ?>
 

$errorMsg"; } ?>

```

---

### Post by bodhi.zazen on 2009-03-17
Would you please try this in firefox :

```
http://127.0.0.1/base
```

---

### Post by KEE on 2009-03-17
yeah thats what Ive used before. it downloads and get locked(cant edit) to my desktop. then I just grab the file to my restarted browser and same thing happens =(

---

### Post by bodhi.zazen on 2009-03-17
Your php is not working.

Are you sure you installed all the necessary packages (php5 and[FONT=monospace] [/FONT]libapache2-mod-php5 ) ?

See :

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/152410](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/152410)

---

### Post by KEE on 2009-03-17
> **bodhi.zazen said:**
> Your php is not working.

Are you sure you installed all the necessary packages (php5 and[FONT=monospace] [/FONT]libapache2-mod-php5 ) ?

See :

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/152410](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/152410)

yeah, Im sure I did, should i try it again?

---

### Post by bodhi.zazen on 2009-03-17
can't hurt :)

---

### Post by KEE on 2009-03-17
yeah i already had it =( maybe its not meant to be ```
me@me-desktop:~$ sudo apt-get install libapache2-mod-php5 php5-cli php5-common php5-cgi
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
php5-cli is already the newest version.
php5-common is already the newest version.
php5-cgi is already the newest version.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libfreebob0 libwildmidi0
  libqt4-opengl libdc1394-22 kdebase-runtime-data-common libsoundtouch1c2
  libqt4-dbus libjack0 phonon libqt4-qt3support libopenspc0 libfftw3-3
  kde-icons-oxygen librasqal0 kdelibs5-data libqtcore4 freepats libqt4-sql
  libqt4-svg phonon-backend-gstreamer libstreamanalyzer0 libphonon4 libqt4-xml
  libcdaudio1 libqt4-network libqt4-designer libqtgui4 libstreams0 libraptor1
  libqt4-script kdebase-runtime-data raptor-utils libmpcdec3 libofa0 libmms0
  libneon27-gnutls libiptcdata0 qt4-qtconfig libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@me-desktop:~$ 

```

---

### Post by bodhi.zazen on 2009-03-17
Try this :

```
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

Then clear your cache and re-start firefox, then try it again.

---

### Post by KEE on 2009-03-17
ok thanks again ill try it in a bit. I just started uploading files and I will do that once the upload is done =)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> Try this :

```
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

Then clear your cache and re-start firefox, then try it again.

totally work man =D thanks so much again =D

---

### Post by bodhi.zazen on 2009-03-18
still waiting for a screen shot of base in firefox :twisted:

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> still waiting for a screen shot of base in firefox :twisted:

ok how do post it here? i might just post it in facebook =)

---

### Post by bodhi.zazen on 2009-03-18
linky ?

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> linky ?

lol kk [http://www.facebook.com/photo.php?pid=30113055&l=f4432aadc2&id=1090594698](http://www.facebook.com/photo.php?pid=30113055&l=f4432aadc2&id=1090594698)

---

### Post by bodhi.zazen on 2009-03-18
very nice, congrats.

do you have snort running ?

I do not see a sensor in base (it lists 0 / 0 ).

If not , fire up snort an you should see it.

like this : [http://bodhizazen.net/img/IDS/base_1.JPG](http://bodhizazen.net/img/IDS/base_1.JPG)

See the non-zero numbers under "Sensors / Total ?

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> very nice, congrats.

do you have snort running ?

I do not see a sensor in base (it lists 0 / 0 ).

If not , fire up snort an you should see it.

like this : [http://bodhizazen.net/img/IDS/base_1.JPG](http://bodhizazen.net/img/IDS/base_1.JPG)

See the non-zero numbers under "Sensors / Total ?

how do i fire up snort?

---

### Post by bodhi.zazen on 2009-03-18
I wrote a small script ;)

See the attachment at the bottom of post 3 

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> I wrote a small script ;)

See the attachment at the bottom of post 3 

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

the file is a shell script (application/x-shellscript)? its in /etc/init.d and its the only one called snort =/ ```
#!/bin/sh -e
#
# Init.d script for Snort in Debian
#
# Copyright (c) 2001 Christian Hammers 
# Copyright (c) 2001-2002 Robert van der Meulen
# Copyright (c) 2002-2004 Sander Smeenk <ssmeenk@debian.org>
# Copyright (c) 2004-2007 Javier Fernandez-Sanguino <jfs@debian.org>
#
# This is free software; you may redistribute it and/or modify
# it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2,
# or (at your option) any later version.
#
# This is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License with
# the Debian operating system, in /usr/share/common-licenses/GPL;  if
# not, write to the Free Software Foundation, Inc., 59 Temple Place,
# Suite 330, Boston, MA 02111-1307 USA
#
### BEGIN INIT INFO
# Provides:          snort
# Required-Start:    $time $network $local_fs
# Required-Stop:     
# Should-Start:      $syslog
# Should-Stop:       
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Lightweight network intrusion detection system
# Description:       Intrusion detection system that will
#                    capture traffic from the network cards and will
#                    match against a set of known attacks.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

test $DEBIAN_SCRIPT_DEBUG && set -v -x

DAEMON=/usr/sbin/snort
NAME=snort
DESC="Network Intrusion Detection System"

. /lib/lsb/init-functions


CONFIG=/etc/snort/snort.debian.conf
# Old (obsolete) way to provide parameters
if [ -f /etc/snort/snort.common.parameters ] ; then
	COMMON=`cat /etc/snort/snort.common.parameters`
elif [ -r /etc/default/snort ] ; then
# Only read this if the old configuration is not present
	. /etc/default/snort
	COMMON="$PARAMS -l $LOGDIR -u $SNORTUSER -g $SNORTGROUP"
fi

test -x $DAEMON || exit 0
test -f $CONFIG && . $CONFIG
test -z "$DEBIAN_SNORT_HOME_NET" && DEBIAN_SNORT_HOME_NET="192.168.0.0/16"

# to find the lib files
cd /etc/snort

running()
{
        PIDFILE=$1
# No pidfile, probably no daemon present
        [ ! -f "$PIDFILE" ] && return 1
        pid=`cat $PIDFILE`
# No pid, probably no daemon present
        [ -z "$pid" ] && return 1
        [ ! -d /proc/$pid ] &&  return 1
        cmd=`cat /proc/$pid/cmdline | tr "\000" "\n"|head -n 1 |cut -d : -f 1`
# No daemon
        [ "$cmd" != "$DAEMON" ] &&  return 1
        return 0
}


check_log_dir() {
# Does the logging directory belong to Snort?
	# If we cannot determine the logdir return without error
	# (we will not check it)
	# This will only be used by people using /etc/default/snort
	[ -n "$LOGDIR" ] || return 0
	[ -n "$SNORTUSER" ] || return 0
	if [ ! -e "$LOGDIR" ] ; then
		log_failure_msg "ERR: logging directory $LOGDIR does not exist"
		return 1
	elif [ ! -d "$LOGDIR" ] ; then
		log_failure_msg "ERR: logging directory $LOGDIR does not exist"
		return 1
	else
		real_log_user=`stat -c %U $LOGDIR`
	# An alternative way is to check if the snort user can create 
	# a file there...
		if [ "$real_log_user" != "$SNORTUSER" ] ; then
			log_failure_msg "ERR: logging directory $LOGDIR does not belong to the snort user $SNORTUSER"
			return 1
		fi
	fi
	return 0
}

check_root()  {
    if [ "$(id -u)" != "0" ]; then
        log_failure_msg "You must be root to start, stop or restart $NAME."
        exit 4
    fi
}

case "$1" in
  start)
        check_root
	log_daemon_msg "Starting $DESC " "$NAME"

        if [ -e /etc/snort/db-pending-config ] ; then
		log_failure_msg "/etc/snort/db-pending-config file found"
		log_failure_msg "Snort will not start as its database is not yet configured."
		log_failure_msg "Please configure the database as described in"
		log_failure_msg "/usr/share/doc/snort-{pgsql,mysql}/README-database.Debian"
		log_failure_msg "and remove /etc/snort/db-pending-config"
		exit 6
	fi

        if ! check_log_dir; then
		log_failure_msg " will not start $DESC!"
		exit 5
	fi
	if [ "$DEBIAN_SNORT_STARTUP" = "dialup" ]; then
		shift
		set +e
		/etc/ppp/ip-up.d/snort "$@"
		ret=$?
                if  [ $ret -eq 0 ] ; then
                  log_end_msg 0
                else
                  log_end_msg 1
                fi
		exit $ret
	fi

	# Usually, we start all interfaces
	interfaces="$DEBIAN_SNORT_INTERFACE"

	# If we are requested to start a specific interface...
	test "$2" && interfaces="$2"

        # If the interfaces list is empty stop (no error)
        if [ -z "$interfaces" ] ; then
            log_progress_msg "no interfaces configured, will not start"
            log_end_msg 0
            exit 0
        fi

	myret=0
	got_instance=0
	for interface in $interfaces; do
		got_instance=1
		log_progress_msg "($interface"

                # Check if the interface is available:
                # - only if iproute is available
                # - the interface exists 
                # - the interface is up
                if ! [ -x /sbin/ip ] || ( ip link show dev "$interface" >/dev/null 2>&1 && [ -n "`ip link show up "$interface" 2>/dev/null`" ] ) ; then

		PIDFILE=/var/run/snort_$interface.pid
                CONFIGFILE=/etc/snort/snort.$interface.conf

                # Defaults:
		fail="failed (check /var/log/syslog and /var/log/snort)"
                run="yes"

                if [ -e "$PIDFILE" ] && running $PIDFILE; then
                        run="no" 
                        # Do not start this instance, it is already runing
                fi

                if [ "$run" = "yes" ] ; then
                    if [ ! -e "$CONFIGFILE" ]; then
                        log_progress_msg "no /etc/snort/snort.$interface.conf found, defaulting to snort.conf"
                        CONFIGFILE=/etc/snort/snort.conf
                    fi

                    set +e
                    /sbin/start-stop-daemon --start --quiet  \
                        --pidfile "$PIDFILE" \
                        --exec $DAEMON -- $COMMON $DEBIAN_SNORT_OPTIONS \
                        -c $CONFIGFILE \
                        -S "HOME_NET=[$DEBIAN_SNORT_HOME_NET]" \
                        -i $interface >/dev/null
                    ret=$?
                    case "$ret" in
			0)
                                log_progress_msg  "...done)"
				;;
			*)
				log_progress_msg "...ERROR: $fail)"
				myret=$(expr "$myret" + 1)
				;;
                     esac
                     set -e
                else
                        log_progress_msg "...already running)"
                fi

                else
                # What to do if the interface is not available
                # or is not up
                        if [ "$ALLOW_UNAVAILABLE" != "no" ] ; then 
                            log_progress_msg "...interface not available)"
                        else 
                            log_progress_msg "...ERROR: interface not available)"
                            myret=$(expr "$myret" + 1)
                        fi
                fi
	done

	if [ "$got_instance" = 0 ] && [ "$ALLOW_UNAVAILABLE" = "no" ]; then
		log_failure_msg "No snort instance found to be started!" >&2
		exit 6
	fi

        if  [ $myret -eq 0 ] ; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
	exit $myret
	;;
  stop)
        check_root
        log_daemon_msg "Stopping $DESC " "$NAME"
    
	if [ "$DEBIAN_SNORT_STARTUP" = "dialup" ]; then
		shift
		set +e
		/etc/ppp/ip-down.d/snort "$@"
		ret=$?
                if  [ $ret -eq 0 ] ; then
                    log_end_msg 0
                else
                  log_end_msg 1
                fi
		exit $ret
	fi

	# Usually, we stop all current running interfaces
	pidpattern=/var/run/snort_*.pid

	# If we are requested to stop a specific interface...
	test "$2" && pidpattern=/var/run/snort_"$2".pid

	got_instance=0
        myret=0
	for PIDFILE in $pidpattern; do
		# This check is also needed, if the above pattern doesn't match
		test -f "$PIDFILE" || continue

		got_instance=1
		interface=$(basename "$PIDFILE" .pid | sed -e 's/^snort_//')

		log_progress_msg "($interface"

		set +e
                if [ ! -e "$PIDFILE" -o -r "$PIDFILE" ] ; then
# Change ownership of the pidfile
		    /sbin/start-stop-daemon --stop --retry 5 --quiet --oknodo \
			--pidfile "$PIDFILE" --exec $DAEMON >/dev/null
                    ret=$?
                    rm -f "$PIDFILE"
                    rm -f "$PIDFILE.lck"
                else
                     log_progress_msg "cannot read $PIDFILE"
                     ret=4
                fi
		case "$ret" in
			0)
                                log_progress_msg  "...done)"
				;;
			*)
				log_progress_msg "...ERROR)"
				myret=$(expr "$myret" + 1)
				;;
		esac
                set -e

	done

	if [ "$got_instance" = 0 ]; then
		log_warning_msg "No running snort instance found"
                exit 0 # LSB demands we don't exit with error here
	fi
        if  [ $myret -eq 0 ] ; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
	exit $myret
	;;
  restart|force-restart|reload|force-reload)
        check_root
	# Usually, we restart all current running interfaces
	pidpattern=/var/run/snort_*.pid

	# If we are requested to restart a specific interface...
	test "$2" && pidpattern=/var/run/snort_"$2".pid

	got_instance=0
	for PIDFILE in $pidpattern; do
		# This check is also needed, if the above pattern doesn't match
		test -f "$PIDFILE" || continue

		got_instance=1
		interface=$(basename "$PIDFILE" .pid | sed -e 's/^snort_//')
		$0 stop $interface || true
		$0 start $interface || true
	done

	if [ "$got_instance" = 0 ]; then
		log_failure_msg "No snort instance found to be stopped!" >&2
                exit 6
	fi
	;;
  status)
# Non-root users can use this (if allowed to)
        log_daemon_msg "Status of snort daemon(s)"
	interfaces="$DEBIAN_SNORT_INTERFACE"
	# If we are requested to check for a specific interface...
	test "$2" && interfaces="$2"
        err=0
        pid=0
	for interface in $interfaces; do
                log_progress_msg " $interface "
                pidfile=/var/run/snort_$interface.pid
                if [ -f  "$pidfile" ] ; then
                        if [ -r "$pidfile" ] ; then
                            pidval=`cat $pidfile`
                            pid=$(expr "$pid" + 1)
                            if ps -p $pidval | grep -q snort; then
                                log_progress_msg "OK"
                            else
				log_progress_msg "ERROR"
				err=$(expr "$err" + 1)
			    fi
                         else
	       		     log_progress_msg "ERROR: cannot read status file"
                             err=$(expr "$err" + 1)
                         fi
                 else
                       log_progress_msg "ERROR"
                       err=$(expr "$err" + 1)
                 fi
        done
        if [ $err -ne 0 ] ; then
            if [ $pid -ne 0 ] ; then
# More than one case where pidfile exists but no snort daemon
# LSB demands a '1' exit value here
                log_end_msg  1
                exit 1
            else
# No pidfiles at all
# LSB demands a '3' exit value here
                log_end_msg  3
                exit 3
            fi
        fi
        log_end_msg  0
        ;;
  config-check)
        log_daemon_msg "Checking $DESC configuration" 
	if [ "$DEBIAN_SNORT_STARTUP" = "dialup" ]; then
		log_failure_msg "Config-check is currently not supported for snort in Dialup configuration"
                log_end_msg  3
                exit 3
	fi

	# usually, we test all interfaces
	interfaces="$DEBIAN_SNORT_INTERFACE"
	# if we are requested to test a specific interface...
	test "$2" && interfaces="$2"

	myret=0
	got_instance=0
	for interface in $interfaces; do
		got_instance=1
		log_progress_msg "interface $interface"

		CONFIGFILE=/etc/snort/snort.$interface.conf
		if [ ! -e "$CONFIGFILE" ]; then
			CONFIGFILE=/etc/snort/snort.conf
		fi
		COMMON=`echo $COMMON | sed -e 's/-D//'`
		set +e
                fail="INVALID"
		if [ -r "$CONFIGFILE" ]; then
                    $DAEMON -T $COMMON $DEBIAN_SNORT_OPTIONS \
			-c $CONFIGFILE \
			-S "HOME_NET=[$DEBIAN_SNORT_HOME_NET]" \
			-i $interface >/dev/null 2>&1
                    ret=$?
                else
                    fail="cannot read $CONFIGFILE"
                    ret=4
                fi
		set -e

		case "$ret" in
			0)
                                log_progress_msg "OK"
				;;
			*)
                                log_progress_msg "$fail"
				myret=$(expr "$myret" + 1)
				;;
		esac
	done
	if [ "$got_instance" = 0 ]; then
		log_failure_msg "no snort instance found to be started!" >&2
		exit 6
	fi

        if  [ $myret -eq 0 ] ; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
	exit $myret
	;;
  *)
	echo "Usage: $0 {start|stop|restart|force-restart|reload|force-reload|status|config-check}"
	exit 1
	;;
esac
exit 0
```

---

### Post by bodhi.zazen on 2009-03-18
Then :

```
sudo /etc/init.d/snort start
```

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> Then :

```
sudo /etc/init.d/snort start
```

```
me@me-desktop:~$ sudo /etc/init.d/snort start
me@me-desktop:~$ 

```hmmm

i still dont get where do i put the "ubuntu.snort.init.txt" in snort shell script? is it just at the bottom?

---

### Post by bodhi.zazen on 2009-03-18
Oh ...

download that script and copy or save it to /etc/init.d/snort

(change the name of the script to snort).

The file should be owned by root

Then make it executable with 

```
sudo chmod a+x /etc/init.d/snort
```

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> Oh ...

download that script and copy or save it to /etc/init.d/snort

(change the name of the script to snort).

The file should be owned by root

Then make it executable with 

```
sudo chmod a+x /etc/init.d/snort
```

should i leave in .txt or copy/past over snort shell script and save? thats what idid but looks nothing happens ```
me@me-desktop:~$ sudo -i
root@me-desktop:~# sudo chmod a+x /etc/init.d/snort
root@me-desktop:~# 


```

---

### Post by KEE on 2009-03-18
o my im getting an error window pop up ? title : bodhis snort script
error: Snort failed to start ... [ok]

---

### Post by bodhi.zazen on 2009-03-18
Did you configure snort as in the Intrusion detection thread ?

Start snort manually and see what errors you get.

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> I wrote a small script ;)

See the attachment at the bottom of post 3 

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

so which part has this problem? im sure ive done them but where do i  start from ```
mysql -u root -p
``` and redo everything? i notice firefox cant use bookmarks any more. i can addthem but the window to name them and finial the add dosent show, so it never adds the bookmark =/

---

### Post by bodhi.zazen on 2009-03-18
no, not the mysql stuff.

Look at post 3 ...

See the section on "configure snort"

You have probably done some of this, but did you edit /etc/snort/snort.conf ?

Manually start snort (as root) with :

```
/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
```

so either sudo -i , become root, and enter that command or

sudo bash -c "/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort"

and tell me what error you are getting.

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> no, not the mysql stuff.

Look at post 3 ...

See the section on "configure snort"

You have probably done some of this, but did you edit /etc/snort/snort.conf ?

Manually start snort (as root) with :

```
/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
```

so either sudo -i , become root, and enter that command or

sudo bash -c "/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort"

and tell me what error you are getting.
thats funny i thought i did those =S
```
root@me-desktop:~# /usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf
ERROR: Unable to open rules file: /etc/snort/snort.conf or /etc/snort//etc/snort/snort.conf
Fatal Error, Quitting..
root@me-desktop:~# 

```

---

### Post by KEE on 2009-03-18
oh i know why now. there is no /etc/snort/snort.conf only /etc/snort/snort.debian.conf and /etc/snort/db-pending-config. theres also a folder there too /etc/snort/rules but no /etc/snort/snort.conf

---

### Post by bodhi.zazen on 2009-03-18
well, cp /etc/snort/snort.debian.conf /etc/snort/snort.conf

But also then make sure you make the necessary edits to /etc/snort/snort.conf ;)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> well, cp /etc/snort/snort.debian.conf /etc/snort/snort.conf

But also then make sure you make the necessary edits to /etc/snort/snort.conf ;)

cp? change path from /etc/snort/snort.debian.conf to /etc/snort/snort.conf?

---

### Post by bodhi.zazen on 2009-03-18
cp is a terminal command for copy

and you need to use sudo (as always).

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> cp is a terminal command for copy

and you need to use sudo (as always).
ok so from this [http://gd.tuwien.ac.at/linuxcommand.org/lts0050.php#cp](http://gd.tuwien.ac.at/linuxcommand.org/lts0050.php#cp)

i understand this is the command? ```
$sudo cp /etc/snort/snort.debian.conf /etc/snort/snort.conf
```

---

### Post by bodhi.zazen on 2009-03-18
Yes, go for it ;)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> Yes, go for it ;)

ok, so it work but i cant figure out what changes to make? /etc/snort/snort.conf is ```
# This file is used for options that are changed by Debian to leave
# the original lib files untouched.
# You have to use "dpkg-reconfigure snort" to change them.

DEBIAN_SNORT_STARTUP="boot"
DEBIAN_SNORT_HOME_NET="192.168.0.0/16"
DEBIAN_SNORT_OPTIONS=""
DEBIAN_SNORT_INTERFACE="eth0"
DEBIAN_SNORT_SEND_STATS="true"
DEBIAN_SNORT_STATS_RCPT="root"
DEBIAN_SNORT_STATS_THRESHOLD="1"
```maybe im not opening in the right editor =/ how do open it in a editor and which do i use?

---

### Post by bodhi.zazen on 2009-03-18
You will need to edit that file and add in things such as your home network and your mysql information.

That file will not work.

did you compile snort from source ?

If so, go back to the section "configure snort" and follow the commands step by step (add a user snort, make a log , copy the files from/usr/src/snort-2.8.3/etc to /etc and what not).

mysql is done, but I do not think you configured snort.

[http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> You will need to edit that file and add in things such as your home network and your mysql information.

That file will not work.

did you compile snort from source ?

If so, go back to the section "configure snort" and follow the commands step by step (add a user snort, make a log , copy the files from/usr/src/snort-2.8.3/etc to /etc and what not).

mysql is done, but I do not think you configured snort.

[http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)i didnt get from source =( i got it from snort.org  its version 2.8.3.2

---

### Post by bodhi.zazen on 2009-03-18
Well, that is the source code.

I trust you also added rules and compiled snort with ./configure , make , make install ?

Well, then just keep following the how to and configure snort.

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> Well, that is the source code.

I trust you also added rules and compiled snort with ./configure , make , make install ?

Well, then just keep following the how to and configure snort.

```
root@me-desktop:~# adduser *
adduser: The user `*' already exists.

```

---

### Post by bodhi.zazen on 2009-03-18
If you already added a user for snort and mysql keep going ...

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> If you already added a user for snort and mysql keep going ...

hey there =D

whats the * mean? ```
cp etc/* /etc/snort/
cp rules/* /etc/snort/rules
```

---

### Post by bodhi.zazen on 2009-03-18
The * is a "wild card"

That means all files.

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> The * is a "wild card"

That means all files.you mean i dont enter it like "*". if the path is different then /etc/snort/rules then I enter the path as it is not as "*" right?  

```
cp: cannot stat `rules/*': No such file or directory

```

---

### Post by bodhi.zazen on 2009-03-18
Not sure what you are asking

rules/* is not the same as /rules/*

the difference is relative vs. absolute path.

If you are following the how to you should be in
[FONT=monospace]
[/FONT]/usr/src/snort-2.8.3.2

Otherwise, the full path is :

```
sudo cp /usr/src/snort-2.8.3/rules/* /etc/snort/rules/
```

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> Not sure what you are asking

rules/* is not the same as /rules/*

the difference is relative vs. absolute path.

If you are following the how to you should be in
[FONT=monospace]
[/FONT]/usr/src/snort-2.8.3.2

Otherwise, the full path is :

```
sudo cp /usr/src/snort-2.8.3/rules/* /etc/snort/rules/
```

hmm no go either ```
root@me-desktop:/usr/src/snort-2.8.3.2# sudo cp /rules/* /etc/snort/rules/
cp: cannot stat `/rules/*': No such file or directory


```

---

### Post by bodhi.zazen on 2009-03-18
did you download a set of rules for snort (from the snort site ? ).

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> did you download a set of rules for snort (from the snort site ? ).have it here but i dont know if its installed now =) 
/usr/src/snortrules-snapshot-2.8

---

### Post by bodhi.zazen on 2009-03-18
ok, well, usually you have to copy the rules into /usr/src/snort-2.8.3.2

Look up in the how to ...

You can try 

sudo cp /usr/src/snortrules-snapshot-2.8/rules/* /etc/snort/rules/

---

### Post by KEE on 2009-03-18
```
root@me-desktop:~# cd /usr/src/snort-2.8.3.2
root@me-desktop:/usr/src/snort-2.8.3.2# tar zxvf /usr/src/snortrules-snapshot-2.8
tar: /usr/src/snortrules-snapshot-2.8: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@me-desktop:/usr/src/snort-2.8.3.2# 

```

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> ok, well, usually you have to copy the rules into /usr/src/snort-2.8.3.2

Look up in the how to ...

You can try 

sudo cp /usr/src/snortrules-snapshot-2.8/rules/* /etc/snort/rules/

ok its there now =D

---

### Post by bodhi.zazen on 2009-03-18
keep going :)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> keep going :)

ok im little lost =d do I go to 4. Compile snort :?

---

### Post by bodhi.zazen on 2009-03-18
No, although we may need to remove and recompile snort.

You are here : [http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)

at "[SIZE=2][B]Configure snort"

[/B]at this step "[/SIZE]We next need to make a few edits to /etc/snort/snort.conf :"

you need to edit /etc/snort/snort.conf and make a few changes.

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> No, although we may need to remove and recompile snort.

You are here : [http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)

at "[SIZE=2][B]Configure snort"

[/B]at this step "[/SIZE]We next need to make a few edits to /etc/snort/snort.conf :"

you need to edit /etc/snort/snort.conf and make a few changes.

ok i got the right .conf there now. just at this part Change "var HOME_NET any" to "var HOME_NET 192.168.0.0/16" (use your netmask here).its the netmask that i dont know what mine is or is it var HOME_NET <mynetmask>? thanks so much bodhi.zazen

---

### Post by bodhi.zazen on 2009-03-18
You can get the information from 

```
sudo ifconfig
```

If you do not know how to interpret that information, post the output ;)

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> You can get the information from 

```
sudo ifconfig
```

If you do not know how to interpret that information, post the output ;)

hold up im still getting this i thought this was repaired =/ before i moved on to that step i thought i should try to finish that part but this didnt work still ```
me@me-desktop:/usr/src/snort-2.8.3.2$ sudo cp rules/* /etc/snort/rules
cp: cannot stat `rules/*': No such file or directory

``` lol never mind we just did that =P

---

### Post by bodhi.zazen on 2009-03-18
you did not follow the directions well and you did not put the rules where they 'belong"

You already copied the rules with this command ;

> sudo cp /usr/src/snortrules-snapshot-2.8/rules/* /etc/snort/rules/

or so you said.

You can confirm this with 

```
ls /etc/snort/rules
```

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> you did not follow the directions well and you did not put the rules where they 'belong"

You already copied the rules with this command ;



or so you said.

You can confirm this with 

```
ls /etc/snort/rules
``````
me@me-desktop:/usr/src/snort-2.8.3.2$ ls /etc/snort/rules
attack-responses.rules  misc.rules        specific-threats.rules
backdoor.rules          multimedia.rules  spyware-put.rules
bad-traffic.rules       mysql.rules       sql.rules
cgi-bin.list            netbios.rules     telnet.rules
chat.rules              nntp.rules        tftp.rules
content-replace.rules   open-test.conf    virus.rules
ddos.rules              oracle.rules      voip.rules
deleted.rules           other-ids.rules   VRT-License.txt
dns.rules               p2p.rules         web-activex.rules
dos.rules               policy.rules      web-attacks.rules
experimental.rules      pop2.rules        web-cgi.rules
exploit.rules           pop3.rules        web-client.rules
finger.rules            porn.rules        web-coldfusion.rules
ftp.rules               rpc.rules         web-frontpage.rules
icmp-info.rules         rservices.rules   web-iis.rules
icmp.rules              scada.rules       web-misc.rules
imap.rules              scan.rules        web-php.rules
info.rules              shellcode.rules   x11.rules
local.rules             smtp.rules
Makefile.am             snmp.rules
me@me-desktop:/usr/src/snort-2.8.3.2$ 

```i cant find "# output database: log, mysql, user= ..." to change it =/ ```

#
# var HOME_NET [10.1.1.0/24,192.168.1.0/24]
#
# MAKE SURE YOU DON'T PLACE ANY SPACES IN YOUR LIST!
#
# or you can specify the variable to be any IP address
# like this:

var HOME_NET 255.255.252.0

#
# output database: log, mysql, user=root password=test dbname=db host=localhost
# output database: alert, postgresql, user=snort dbname=snort
# output database: log, odbc, user=snort dbname=snort
# output database: log, mssql, dbname=snort user=snort password=test
# output database: log, oracle, dbname=snort user=snort password=test


```

---

### Post by bodhi.zazen on 2009-03-18
1. Your rules look fine.

2. I edited your post to show you a few things.

first "var HOME_NET 255.255.252.0" is wrong.

It should be something like 192.68.0.0/16

second the output section is near the bottom. Open an editor such as gedit and use the search functions.

```
gksu gedit /etc/snort/snort.conf
```

You will need to be more precise in the config file. Try to follow the directions.

---

### Post by KEE on 2009-03-18
> **bodhi.zazen said:**
> 1. Your rules look fine.

2. I edited your post to show you a few things.

first "var HOME_NET 255.255.252.0" is wrong.

It should be something like 192.68.0.0/16

second the output section is near the bottom. Open an editor such as gedit and use the search functions.

```
gksu gedit /etc/snort/snort.conf
```

You will need to be more precise in the config file. Try to follow the directions.ok i dont know where my netmask is xD
```

me@me-desktop:~$ sudo ifconfig
[sudo] password for me: 
eth0      Link encap:Ethernet  HWaddr 00:0d:60:23:0d:13  
          inet addr:70.66.217.176  Bcast:70.66.219.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:6913608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9041754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:503974701 (503.9 MB)  TX bytes:900753983 (900.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84314 (84.3 KB)  TX bytes:84314 (84.3 KB)
```

---

### Post by KEE on 2009-03-18
I couldnt find any output database other then this ```
# output database: log, mysql, user=root password=test dbname=db host=localhost
# output database: alert, postgresql, user=snort dbname=snort
# output database: log, odbc, user=snort dbname=snort
# output database: log, mssql, dbname=snort user=snort password=test
# output database: log, oracle, dbname=snort user=snort password=test
```

---

### Post by bodhi.zazen on 2009-03-19
Ah, it appears you are connected directly to the internet without a router.

As such your ipaddress may change. I am not sure what to put here as I usually am behind a router.

Second, you need to edit this line :

> # output database: log, mysql, user=root password=test dbname=db host=localhost

First , remove the #

then change "root" to your mysql user
"dbname" to the name you used for your mysql database
and
"password" to the password you gave for your mysql user on mysql.

---

### Post by KEE on 2009-03-19
> **bodhi.zazen said:**
> Ah, it appears you are connected directly to the internet without a router.

As such your ipaddress may change. I am not sure what to put here as I usually am behind a router.

Second, you need to edit this line :



First , remove the #

then change "root" to your mysql user
"dbname" to the name you used for your mysql database
and
"password" to the password you gave for your mysql user on mysql.

oh I see, well i guess i should stop here then =( it was very nice of you to help me through this and I learned a lot about linux terminal xD sorry, i didnt know i had that issue with my ip address =( take care bodhi.zazen =D

---

### Post by bodhi.zazen on 2009-03-19
naw, keep going

For now use your ip address

var HOME_NET 70.66.217.176

---

### Post by KEE on 2009-03-19
> **bodhi.zazen said:**
> naw, keep going

For now use your ip address

var HOME_NET 70.66.217.176 alright I will =D

---

### Post by KEE on 2009-03-19
im still getting that error "failed to start" i think i need to remove my old user names and passwords cause i might of cause the a mix up xD how do you remove all user names and passwords? maybe even the msql name too =( Thanks for your help in this =)

---

### Post by bodhi.zazen on 2009-03-19
I would not mess with mysql as the problem is most likely with the snort config.

Could you post the lines you edited (not the entire file as it is quite long).

---

### Post by KEE on 2009-03-20
> **bodhi.zazen said:**
> I would not mess with mysql as the problem is most likely with the snort config.

Could you post the lines you edited (not the entire file as it is quite long).

well i tried a couple of things but the config meet be messed up (my fault) xD i thin i should start over with the snort config =/  ```
# Step #1: Set the network variables:
#
# You must change the following variables to reflect your local network. The
# variable is currently setup for an RFC 1918 address space.
#
# You can specify it explicitly as: 
#
# var HOME_NET 10.1.1.0/24
#
# or use global variable $<interfacename>_ADDRESS which will be always
# initialized to IP address and netmask of the network interface which you run
# snort at.  Under Windows, this must be specified as
# $(<interfacename>_ADDRESS), such as:
# $(\Device\Packet_{12345678-90AB-CDEF-1234567890AB}_ADDRESS)
#
# var HOME_NET $eth0_ADDRESS
#
# You can specify lists of IP addresses for HOME_NET
# by separating the IPs with commas like this:
#
# var HOME_NET [10.1.1.0/24,192.168.1.0/24]
#
# MAKE SURE YOU DON'T PLACE ANY SPACES IN YOUR LIST!
#
# or you can specify the variable to be any IP address
# like this:

var HOME_NET 96.54.115.44

# Set up the external network addresses as well.  A good start may be "any"
var EXTERNAL_NET !$HOME_NET
var EXTERNAL_NET !$HOME_NET
var RULE_PATH /etc/snort/rules
output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost
output database: alert, postgresql, user=snort dbname=snort
# output database: log, odbc, user=snort dbname=snort
# output database: log, mssql, dbname=snort user=snort password=test
# output database: log, oracle, dbname=snort user=snort password=test









```

---

### Post by bodhi.zazen on 2009-03-20
I see t things :)

1. > var HOME_NET 96.54.115.44

This is not your ip address. You can see your ipaddress with :

sudo ifconfig

and the last time you posted the output your ipaddress was [/b]70.66.217.176[/b]

> eth0      Link encap:Ethernet  HWaddr 00:0d:60:23:0d:13  [FONT=monospace]
[/FONT] inet addr:70.66.217.176  Bcast:70.66.219.255  Mask:255.255.252.0[FONT=monospace]
[/FONT] UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1[FONT=monospace]
[/FONT] RX packets:6913608 errors:0 dropped:0 overruns:0 frame:0[FONT=monospace]
[/FONT] TX packets:9041754 errors:0 dropped:0 overruns:0 carrier:0[FONT=monospace]
[/FONT] collisions:0 txqueuelen:1000 [FONT=monospace]
[/FONT] RX bytes:503974701 (503.9 MB)  TX bytes:900753983 (900.7 MB)

so you need the correct ip address on this line.



2. You have two "output lines" uncommented.

> output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost
output database: alert, postgresql, user=snort dbname=snort[/qutoe]

you need to comment out the second one , like this ;

```
output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost
# output database: alert, postgresql, user=snort dbname=snort
```


3. Last, you understand the line [quote]output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost

you need to change the variables

mysql_user_name
psswed
snortme

to the information you added when you configured mysql ?

4. You may need to re-start mysql (I doubt it, but can not hurt)

```
sudo /etc/init.d/mysql restart
```

---

### Post by KEE on 2009-03-20
> **bodhi.zazen said:**
> I see t things :)

1. 

This is not your ip address. You can see your ipaddress with :

sudo ifconfig

and the last time you posted the output your ipaddress was [/b]70.66.217.176[/b]



so you need the correct ip address on this line.
```
me@me-desktop:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
me@me-desktop:~$ 




2. You have two "output lines" uncommented.

[quote]output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost
output database: alert, postgresql, user=snort dbname=snort[/qutoe]

you need to comment out the second one , like this ;

[code]output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost
# output database: alert, postgresql, user=snort dbname=snort
```


3. Last, you understand the line 

you need to change the variables

mysql_user_name
psswed
snortme

to the information you added when you configured mysql ?

4. You may need to re-start mysql (I doubt it, but can not hurt)

```
sudo /etc/init.d/mysql restart
```

well heres what i got for sudo ifconfig```
eth0      Link encap:Ethernet  HWaddr 00:0d:60:23:0d:13  
          inet addr:96.54.115.44  Bcast:96.54.115.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:17672779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17404351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1514096023 (1.5 GB)  TX bytes:2005261126 (2.0 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3232 (3.2 KB)  TX bytes:3232 (3.2 KB)

``` ill that edit it and i might need to try that msql restart thing too =) brb

---

### Post by bodhi.zazen on 2009-03-20
Ah, so your ip address is in fact changing rapidly.

Try the variable as suggested i nth econfig file :

> use global **variable $<interfacename>_ADDRESS** which will be always[FONT=monospace]
[/FONT]# initialized to IP address and netmask of the network interface which you run[FONT=monospace]
[/FONT]# snort at.

so ```
var HOME_NET $<interfacename>_ADDRESS
```

I am not sure if you need to change $<interfacename> to eth0 or not, you will have to try and watch snort for errors as you start it manually.

```
/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
```

YOU NEED TO START SNORT AS ROOT, so either sudo -i then enter that command.

---

### Post by KEE on 2009-03-20
> **bodhi.zazen said:**
> ;

```
output database: log, mysql, user=mysql_user_name password=psswed dbname=snortme host=localhost
# output database: alert, postgresql, user=snort dbname=snort
```



ok, but do mean that i just left the "#" out? sorry that is a typo its in there =)

---

### Post by KEE on 2009-03-20
> **bodhi.zazen said:**
> Ah, so your ip address is in fact changing rapidly.

Try the variable as suggested i nth econfig file :



so ```
var HOME_NET $<interfacename>_ADDRESS
```

I am not sure if you need to change $<interfacename> to eth0 or not, you will have to try and watch snort for errors as you start it manually.

```
/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
```

YOU NEED TO START SNORT AS ROOT, so either sudo -i then enter that command.

where would i find my interfacename? you mean the os?

---

### Post by bodhi.zazen on 2009-03-20
interface name is eth0 and is your network card and is listed with

sudo ifconfig

I would start with the syntax as in the config file :

var HOME_NET $<interfacename>_ADDRESS

---

### Post by KEE on 2009-03-20
> **bodhi.zazen said:**
> interface name is eth0 and is your network card and is listed with

sudo ifconfig

I would start with the syntax as in the config file :

var HOME_NET $<interfacename>_ADDRESS

pardon? do i put  this whole thing? ```
var HOME_NET $eth0      Link encap:Ethernet  HWaddr 00:0d:60:23:0d:13  
          inet addr:96.54.115.44  Bcast:96.54.115.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:17672779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17404351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1514096023 (1.5 GB)  TX bytes:2005261126 (2.0 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3232 (3.2 KB)  TX bytes:3232 (3.2 KB)_ADDRESS
```

---

### Post by bodhi.zazen on 2009-03-20
no

In the snort confing file you need to define the variable for HOME_NET

so use

```
var HOME_NET $<interfacename>_ADDRESS
``` 

work for word, as is , in the appropriate place in the config file.

You also really need to start snort manually to see the error message.

---

