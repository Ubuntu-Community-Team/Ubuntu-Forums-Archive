---
title: "Zenoss core on Ubuntu server 9.04"
date: 2009-05-25
forum: Server Platforms
---

### Post by b.ng on 2009-05-25
Hi,

I tried to install Zenoss core on Ubuntu server 9.04, but it reported failed to install after a lengthy compilation and leaving a lengthy log.

Anyone here could successfully install that?

Thanks.

---

### Post by hackeron on 2009-07-10
I'm also having trouble compiling it, getting:

```

build/m4/check_cc.m4:8: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
autoheader: '/usr/bin/autom4te' failed with exit status: 1
/bin/sh: ./configure: not found
make[2]: Entering directory `/data/zenossinst/build/wmi-1.2.6/Samba/source'
make[2]: *** No rule to make target `proto'. Stop.
make[2]: Leaving directory `/data/zenossinst/build/wmi-1.2.6/Samba/source'
make[1]: Leaving directory `/data/zenossinst/build/wmi-1.2.6'
make[1]: Entering directory `/data/zenossinst/build/wmi-1.2.6'
cd Samba/source ;				\
	./autogen.sh ;					\
	CPPFLAGS="-I//usr/local/zenoss/include/python2.4"			\
	./configure --without-readline --enable-debug ;	\
	make proto bin/wmic bin/winexe libraries ; 		\
	touch pywmi-build
./autogen.sh: running script/mkversion.sh
./script/mkversion.sh: 'version.h' created for Samba("4.0.0tp4-SVN-build-UNKNOWN")
./autogen.sh: running autoheader -I. -Ilib/replace
build/m4/check_cc.m4:8: error: AC_REQUIRE: circular dependency of AC_GNU_SOURCE
lib/replace/autoconf-2.60.m4:169: AC_USE_SYSTEM_EXTENSIONS is expanded from...
../../lib/autoconf/specific.m4:332: AC_GNU_SOURCE is expanded from...
lib/replace/autoconf-2.60.m4:169: AC_USE_SYSTEM_EXTENSIONS is expanded from...
build/m4/check_cc.m4:8: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
autoheader: '/usr/bin/autom4te' failed with exit status: 1
/bin/sh: ./configure: not found
make[2]: Entering directory `/data/zenossinst/build/wmi-1.2.6/Samba/source'
make[2]: *** No rule to make target `proto'. Stop.
make[2]: Leaving directory `/data/zenossinst/build/wmi-1.2.6/Samba/source'
cd Samba/source ; \
	cp bin/winexe //usr/local/zenoss/bin ; \
	cp bin/wmic //usr/local/zenoss/bin ; \
	cp bin/shared/*async_wmi_lib.so.0* //usr/local/zenoss/lib/python
cp: cannot stat `bin/winexe': No such file or directory
cp: cannot stat `bin/wmic': No such file or directory
cp: cannot stat `bin/shared/*async_wmi_lib.so.0*': No such file or directory
make[1]: *** [pywmi-installed] Error 1
make[1]: Leaving directory `/data/zenossinst/build/wmi-1.2.6'

```

Any ideas?

---

### Post by hackeron on 2009-07-10
[http://dev.zenoss.org/trac/ticket/4994](http://dev.zenoss.org/trac/ticket/4994) < :(

---

