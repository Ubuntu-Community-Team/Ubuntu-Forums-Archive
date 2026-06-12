---
title: "Gemalto USB Shell Token V2 under Ubuntu"
date: 2010-12-09
forum: Security
---

### Post by Matthai on 2010-12-09
Hi,
I have Gemalto dot NET USB Shell Token V2 ([http://www.gemalto.com/products/dotnet_card/index.html](http://www.gemalto.com/products/dotnet_card/index.html)) and I am trying to use it under Ubuntu Maverick.

I have dowloaded .NET PKCS#11 library (from here: [http://www.gemalto.com/products/dotnet_card/resources/libraries.html?toggler=0](http://www.gemalto.com/products/dotnet_card/resources/libraries.html?toggler=0)).

In the zip file there is a manual (PKCS#11_Libs_.NET_Linux_User_Guide.pdf) which states that for Ubuntu a package libgemaltodotnetp11_2.1.0-1ubuntu1_i386.deb should be installed.

However, in the PKCS#11 library package (zip file), there is no .deb package, but there is a script, which configures and compiles library on the system.

When I run this script (sh run_compile.sh), I got an error:

configure: error: winscard.h not found, install pcsc-lite, or use
PCSC_CFLAGS=... ./configure

The problem is, there is no pcsc-lite package in Ubuntu. I have installed libpcsc-perl, libccid, pcsc-tools, libpcsclite-dev and libpcsclite1.

pcsc_scan recognizes the device.

Any help?

---

### Post by janeku on 2011-01-11
Oh my friend.
It looks like we are stuck with the same problem.
I'm trying to install this token too, but no luck.
I can't find any additional info except the one from Gemalto but this one is so poor :(
They are saying about installing it thru Mozilla but when it comes to point to say where to search for .so file , BANG, there is no such directory on my comp. 
I must say I use 10.04 Lucid.
I'll try to message Gemalto to try find out this problem.
Regards my friend

Addition:

Please see this thread. I think this will be solution for our problem.
[http://ubuntuforums.org/showthread.php?t=1221961&highlight=GEMALTO]("http://ubuntuforums.org/showthread.php?t=1221961&highlight=GEMALTO")

---

### Post by Matthai on 2011-01-12
In fact there is a simple solution: open the script, search for "-I/usr/include/smartcard" and REPLACE it with "-I/usr/include/PCSC".

It is also good to install zlib1g-dev package. Then it works.

PIN change and USB token management is then done through web interface, actually Gemalto offers some XPI extension for Firefox for doing that.

I don't have a time for writing a guide, but thing works fine. But yes, it would be nice to have .deb package and GUI python application for that... :D

---

### Post by janeku on 2011-01-15
Interesting.
As a total newbie to this OS, changing this line will makerun-compile.sh to run properly ?
And then what ?
Please forgive me, but really I still do not know how to continue, so here is attached Gemalto's file , please post a guide how to properly install this token.[http://rapidshare.com/files/442122857/5777_Linux_P11DotNET.zip]("http://rapidshare.com/files/442122857/5777_Linux_P11DotNET.zip")

I'll try to do my own best but :( :) I'm just a rookie using Ububtu for less than a month.

Ok I think I made it, but I can't see SO file in my pkcs11 dir in /usr/lib/pkcs11.
Here is output of my terminal :

```
log.cpp:1497: warning: unused parameter ‘pMechanismList’
log.cpp:1497: warning: unused parameter ‘mechanismListLen’
log.cpp:1497: warning: unused parameter ‘result’
log.cpp:1523: warning: unused parameter ‘t’
log.cpp:1523: warning: unused parameter ‘result’
log.cpp:1981: warning: unused parameter ‘pInfo’
log.cpp:1981: warning: unused parameter ‘result’
log.cpp:2000: warning: unused parameter ‘f’
log.cpp:2000: warning: unused parameter ‘result’
log.cpp:2117: warning: unused parameter ‘f’
log.cpp:2117: warning: unused parameter ‘result’
log.cpp:2142: warning: unused parameter ‘pInfo’
log.cpp:2142: warning: unused parameter ‘result’
log.cpp:2165: warning: unused parameter ‘t’
log.cpp:2165: warning: unused parameter ‘result’
log.cpp:2199: warning: unused parameter ‘a_pMethod’
libtool: compile:  g++ -DPACKAGE_NAME=\"libgtop11dotnet\" -DPACKAGE_TARNAME=\"libgtop11dotnet\" -DPACKAGE_VERSION=\"2.1.3.2\" "-DPACKAGE_STRING=\"libgtop11dotnet 2.1.3.2\"" -DPACKAGE_BUGREPORT=\"hotline@gemalto.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"libgtop11dotnet\" -DVERSION=\"2.1.3.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DHAVE_PTHREAD=1 -DHAVE_LPCTSTR=1 -DHAVE_LPCSTR=1 -I. -I. -I../cppMarshaller -I../PKCS11Module2 -I../PKCS11Module2/rsa -I/usr/include/PCSC -DINCLUDE_EVENTING=1 -DCRYPTOKI_EXPORTS=1 -DUNIX -Wall -Wextra -pedantic -g -O2 -MT log.lo -MD -MP -MF .deps/log.Tpo -c log.cpp -o log.o >/dev/null 2>&1
/bin/bash ../libtool --tag=CXX --mode=link g++  -g -O2   -o libgtop11dotnet.la -rpath /usr/lib -shared Array.lo Marshaller.lo PCSC.lo algo_des.lo algo_md5.lo algo_sha1.lo algo_sha256.lo algo_utils.lo application.lo attrcert.lo beroctet.lo cardcache.lo cardmoduleservice.lo certificateobject.lo cert_utils.lo critsect.lo dataobject.lo des.lo digest.lo error.lo event.lo keyobject.lo md5.lo mutex.lo pkcs11.lo privatekeyobject.lo publickeyobject.lo cr_digit.lo cr_nn.lo cr_random.lo cr_rsa.lo rsaprivatekeyobject.lo rsapublickeyobject.lo sctoken.lo secretkeyobject.lo session.lo sha1.lo sha256.lo slot.lo stdafx.lo storageobject.lo symmalgo.lo tdes.lo template.lo thread.lo timer.lo transaction.lo util.lo x509cert.lo x509pubkeycertobject.lo log.lo  -lpcsclite   -lpthread -lz
libtool: link: g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.4.3/crtbeginS.o  .libs/Array.o .libs/Marshaller.o .libs/PCSC.o .libs/algo_des.o .libs/algo_md5.o .libs/algo_sha1.o .libs/algo_sha256.o .libs/algo_utils.o .libs/application.o .libs/attrcert.o .libs/beroctet.o .libs/cardcache.o .libs/cardmoduleservice.o .libs/certificateobject.o .libs/cert_utils.o .libs/critsect.o .libs/dataobject.o .libs/des.o .libs/digest.o .libs/error.o .libs/event.o .libs/keyobject.o .libs/md5.o .libs/mutex.o .libs/pkcs11.o .libs/privatekeyobject.o .libs/publickeyobject.o .libs/cr_digit.o .libs/cr_nn.o .libs/cr_random.o .libs/cr_rsa.o .libs/rsaprivatekeyobject.o .libs/rsapublickeyobject.o .libs/sctoken.o .libs/secretkeyobject.o .libs/session.o .libs/sha1.o .libs/sha256.o .libs/slot.o .libs/stdafx.o .libs/storageobject.o .libs/symmalgo.o .libs/tdes.o .libs/template.o .libs/thread.o .libs/timer.o .libs/transaction.o .libs/util.o .libs/x509cert.o .libs/x509pubkeycertobject.o .libs/log.o   /usr/lib/libpcsclite.so -lpthread -lz -L/usr/lib/gcc/i486-linux-gnu/4.4.3 -L/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.4.3/../../.. -L/usr/lib/i486-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.4.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crtn.o    -Wl,-soname -Wl,libgtop11dotnet.so.0 -o .libs/libgtop11dotnet.so.0.0.0
libtool: link: (cd ".libs" && rm -f "libgtop11dotnet.so.0" && ln -s "libgtop11dotnet.so.0.0.0" "libgtop11dotnet.so.0")
libtool: link: (cd ".libs" && rm -f "libgtop11dotnet.so" && ln -s "libgtop11dotnet.so.0.0.0" "libgtop11dotnet.so")
libtool: link: ( cd ".libs" && rm -f "libgtop11dotnet.la" && ln -s "../libgtop11dotnet.la" "libgtop11dotnet.la" )
make[1]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
make[1]: Entering directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2'
+ make install DESTDIR=/tmp/p11dotnetv2
Making install in PKCS11Module2
make[1]: Entering directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
make[2]: Entering directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
test -z "/usr/lib" || mkdir -p -- "/tmp/p11dotnetv2/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libgtop11dotnet.la' '/tmp/p11dotnetv2/usr/lib/libgtop11dotnet.la'
libtool: install: /usr/bin/install -c .libs/libgtop11dotnet.so.0.0.0 /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so.0.0.0
libtool: install: (cd /tmp/p11dotnetv2/usr/lib && { ln -s -f libgtop11dotnet.so.0.0.0 libgtop11dotnet.so.0 || { rm -f libgtop11dotnet.so.0 && ln -s libgtop11dotnet.so.0.0.0 libgtop11dotnet.so.0; }; })
libtool: install: (cd /tmp/p11dotnetv2/usr/lib && { ln -s -f libgtop11dotnet.so.0.0.0 libgtop11dotnet.so || { rm -f libgtop11dotnet.so && ln -s libgtop11dotnet.so.0.0.0 libgtop11dotnet.so; }; })
libtool: install: /usr/bin/install -c .libs/libgtop11dotnet.lai /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.la
libtool: install: warning: remember to run `libtool --finish /usr/lib'
make  install-exec-hook
make[3]: Entering directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
/bin/mkdir -p /tmp/p11dotnetv2//usr/lib/pkcs11
cd /tmp/p11dotnetv2//usr/lib/pkcs11 ; rm -f libgtop11dotnet.so ; ln -s ../libgtop11dotnet.so
make[3]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
make[1]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2/PKCS11Module2'
make[1]: Entering directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2'
make[2]: Entering directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2'
make[1]: Leaving directory `/home/petrika/Desktop/5777_Linux_P11DotNET/libgtop11dotnet-2.1.3.2'
+ echo --------------------------------
--------------------------------
+ find /tmp/p11dotnetv2 -print
+ ls -ld /tmp/p11dotnetv2 /tmp/p11dotnetv2/usr /tmp/p11dotnetv2/usr/lib /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.la /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so.0 /tmp/p11dotnetv2/usr/lib/pkcs11 /tmp/p11dotnetv2/usr/lib/pkcs11/libgtop11dotnet.so /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so.0.0.0
drwxr-xr-x 3 root root    4096 2011-01-15 13:19 /tmp/p11dotnetv2
drwxr-xr-x 3 root root    4096 2011-01-15 13:19 /tmp/p11dotnetv2/usr
drwxr-xr-x 3 root root    4096 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib
-rwxr-xr-x 1 root root    1011 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.la
lrwxrwxrwx 1 root root      24 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so -> libgtop11dotnet.so.0.0.0
lrwxrwxrwx 1 root root      24 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so.0 -> libgtop11dotnet.so.0.0.0
-rwxr-xr-x 1 root root 2689253 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib/libgtop11dotnet.so.0.0.0
drwxr-xr-x 2 root root    4096 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib/pkcs11
lrwxrwxrwx 1 root root      21 2011-01-15 13:19 /tmp/p11dotnetv2/usr/lib/pkcs11/libgtop11dotnet.so -> ../libgtop11dotnet.so
+ echo --------------------------------
--------------------------------
+ echo Done.
Done.

```

Where is this d*mned SO file ???

---

### Post by Yustas2 on 2012-08-21
5777_Linux_P11DotNET.zip is not available for now ((
May be somebody has it?

---

### Post by oldos2er on 2012-08-21
Yustas2, please start a new thread for your question; this one's two years old.

---

