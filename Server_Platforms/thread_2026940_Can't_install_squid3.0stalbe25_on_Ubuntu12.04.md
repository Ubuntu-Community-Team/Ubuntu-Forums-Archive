---
title: "Can't install squid3.0stalbe25 on Ubuntu12.04"
date: 2012-07-16
forum: Server Platforms
---

### Post by slinbody on 2012-07-16
Hi, all
I run "apt-get update" after installing Ubuntu 12.04 server i386.
Then download squid-3.0.STABLE25.tar.gz to install it.
After ./configure with my option, I encounter the following message when I run 'make':

Making all in src
make[1]: Entering directory `/usr/local/src/squid-3.0.STABLE25/src'
depbase=`echo AuthUser.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
        /bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -DDEFAULT_CONFIG_FILE=\"/etc/squid3/squid.conf\" -I. -I../include -I. -I. -I../include -I../include -I../lib/libTrie/include    -Werror -Wall -Wpointer-arith -Wwrite-strings -Wcomments -fhuge-objects -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT AuthUser.lo -MD -MP -MF $depbase.Tpo -c -o AuthUser.lo AuthUser.cc &&\
        mv -f $depbase.Tpo $depbase.Plo
 g++ -DHAVE_CONFIG_H -DDEFAULT_CONFIG_FILE=\"/etc/squid3/squid.conf\" -I. -I../include -I. -I. -I../include -I../include -I../lib/libTrie/include -Werror -Wall -Wpointer-arith -Wwrite-strings -Wcomments -fhuge-objects -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT AuthUser.lo -MD -MP -MF .deps/AuthUser.Tpo -c AuthUser.cc -o AuthUser.o
g++: warning: switch &#8216;-fhuge-objects&#8217; is no longer supported
AuthUser.cc: In static member function &#8216;static void AuthUser::CachedACLsReset()&#8217;:
AuthUser.cc:161:17: error: variable &#8216;username&#8217; set but not used [-Werror=unused-but-set-variable]
cc1plus: all warnings being treated as errors
make[1]: *** [AuthUser.lo] Error 1
make[1]: Leaving directory `/usr/local/src/squid-3.0.STABLE25/src'
make: *** [all-recursive] Error 1

Does anyone has good ideas to solve it??

---

### Post by Cheesemill on 2012-07-16
Why are you trying to compile it anyway? There is a newer version in the repos.
```
sudo apt-get install squid3
```

---

### Post by slinbody on 2012-07-16
> **Cheesemill said:**
> Why are you trying to compile it anyway? There is a newer version in the repos.
```
sudo apt-get install squid3
```
I don't run 'sudo apt-get install squid3' because:
1. I want to tune some options.
2. There are other servers with squid3.0 stable25 version. I want all of them with the same verion.

---

