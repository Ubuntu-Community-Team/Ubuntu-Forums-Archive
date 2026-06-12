---
title: "Probs installing Authen::Libwrap"
date: 2009-12-21
forum: Server Platforms
---

### Post by BarryDocks on 2009-12-21
Hi there, 

Trying to install the perl module Authen::Libwrap to enable https for webmin, but keep getting this error when compiling the module:
Executing /usr/bin/perl Makefile.PL  && make ..
                                                                                                    
```
# running Build.PL 
/usr/bin/perl Build.PL
enter include directory to use: [/usr/include ]/usr/include 
enter library directory to use: [/usr/lib ]/usr/lib 
Checking whether your kit is complete...
Looks good

Checking prerequisites...
Looks good

Creating new 'Build' script for 'Authen-Libwrap' version '0.21'
/usr/bin/perl Build --makefile_env_macros 1
Copying lib/Authen/Libwrap.pm -> blib/lib/Authen/Libwrap.pm
lib/Authen/Libwrap.xs -> lib/Authen/Libwrap.c
Error: Function definition too short '/ * EOF * /' in Libwrap.xs, line 32
cc -I/usr/lib/perl/5.8/CORE -DXS_VERSION="0.21" -DVERSION="0.21" -fPIC -I/usr/include -c -D_REENTRAN
T -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARG
EFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -o lib/Authen/Libwrap.o lib/Authen/Libwrap.c
lib/Authen/Libwrap.xs:9:18: error: tcpd.h: No such file or directory
error building lib/Authen/Libwrap.o from 'lib/Authen/Libwrap.c' at /usr/share/perl5/ExtUtils/CBuilde
r/Base.pm line 108.
make: *** [all] Error 2
```

Can any one help?

Thanks

---

### Post by Webcreature on 2010-04-28
You have to install libwrap0 and libwrap0-dev by
[INDENT]**apt-get install libwrap0 libwrap0-dev**
[/INDENT]as of this package delivers tcpd.h (and more).
 
*(I also had this problem several times. I post this here to have a location to find the solution when I forget it the next time ...)*

---

### Post by BarryDocks on 2010-04-29
thanks!

---

