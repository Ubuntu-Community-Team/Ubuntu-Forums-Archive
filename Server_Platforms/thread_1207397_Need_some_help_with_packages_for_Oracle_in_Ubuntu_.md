---
title: "Need some help with packages for Oracle in Ubuntu Server 8.04 64 bit"
date: 2009-07-08
forum: Server Platforms
---

### Post by dragos2 on 2009-07-08
I am in the need for some help.

I am trying to install Oracle Enterprise on Ubuntu Server 8.04 64 bit.

After setting tons of requirements the installation failed at 88%.

In this [http://www.pythian.com/news/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon](http://www.pythian.com/news/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon) guide for 7.10 these are the recommended packages
apt-get install gcc make binutils libaio1 gawk ksh libc6-dev rpm libmotif3 alien lsb-rpm libtool

but here are other packages specified
[http://download.oracle.com/docs/cd/B28359_01/install.111/b32002/pre_install.htm#CIHFICFD](http://download.oracle.com/docs/cd/B28359_01/install.111/b32002/pre_install.htm#CIHFICFD)

like for Suse
binutils-2.16.91.0.5
compat-libstdc++-5.0.7-22.2
gcc-4.1.0
gcc-c++-4.1.0
glibc-2.4-31.2
glibc-32bit-2.4-31.2 (32 bit)
glibc-devel-2.4
glibc-devel-32bit-2.4 (32 bit)
libaio-0.3.104
libaio-32bit-0.3.104 (32 bit)
libaio-devel-0.3.104
libelf-0.8.5
libgcc-4.1.0
libstdc++-4.1.0
libstdc++-devel-4.1.0
make-3.80
sysstat-6.0.2

What other packages should I install ?

---

### Post by guilly on 2009-07-08
I've attempted to install oracle a few times on Ubuntu with no success. I would suggest just to install it on SUSE. You'll probably have more success...

---

### Post by dragos2 on 2009-07-08
I dedicated too much time to quit now, the Oracle installation goes fine
until 88% where it fails because one the of the dependencies.

I installed glibc from source (took 30 minutes) and I installed only 
one deb from those 6 generated the one named glibc-6-source.deb or
similar name.

But I need this last packet now I guess   compat-libstdc++
and I found only rpm's. I will try tomorrow with alien,
maybe it will work.

I even changed the sh -> dash to sh -> bash to make the
installation more compatible.

I am deeply sorry, Ubuntu Server 8.04 is a great server and
I want to install Oracle Enterprise on it, I spent too much time
with the prerequisites to change to another OS.

So can anyone please assist me further in this process, I am
almost at the end.

---

### Post by dragos2 on 2009-07-08
This are the last lines from the install log
```

INFO: gcc -m32 -o /oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib/extproc32 -L/oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib32/ -L/oracle/u01/app/oracle/product/11.1.0/db_1/lib32/ -L/oracle/u01/app/oracle/product/11.1.0/db_1/lib32/stubs/   /oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib32/hormc.o   /oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib32/homts.o		  -lagtsh -lpthread -lclntsh   `cat /oracle/u01/app/oracle/product/11.1.0/db_1/lib32/sysliblist` -Wl,-rpath,/oracle/u01/app/oracle/product
INFO: /11.1.0/db_1/lib32 -lm    `cat /oracle/u01/app/oracle/product/11.1.0/db_1/lib32/sysliblist` -ldl -lm   -L/oracle/u01/app/oracle/product/11.1.0/db_1/lib32 

INFO: /usr/bin/ld: cannot find -lagtsh

INFO: collect2: ld returned 1 exit status

INFO: make[1]: *** [/oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib/extproc32] Error 1

INFO: make[1]: Leaving directory `/oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib'

INFO: make: *** [extproc32] Error 2

INFO: End output from spawned process.
INFO: ----------------------------------
INFO: Exception thrown from action: make
Exception Name: MakefileException
Exception String: Error in invoking target 'all_no_orcl' of makefile '/oracle/u01/app/oracle/product/11.1.0/db_1/rdbms/lib/ins_rdbms.mk'. See '/oracle/u01/app/oraInventory/logs/installActions2009-07-08_09-20-30AM.log' for details.
Exception Severity: 1


```

How can I figure out what is the actual error ?

---

### Post by GusPS on 2009-07-23
I'm trying this on Jaunty Server 64 bits and I get stuck at 65%. It's in the Linking phase.

```
Error in invoking target 'collector' of makefile '/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/ins_emdb.mk'.
```Previous log:

```
INFO: /ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/snmccolm.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmccol.a(nmccole.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbuf.a(nmcbuft.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g
INFO: /product/10.2.0/db_1/sysman/lib/libnmcbuf.a(nmcbufw.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbuf.a(nmcbufu.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbuf.a(snmcbufm.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbu
INFO: f.a(nmcbuff.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib//libnmadbg.a(nmadbg.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib//libnmadbg.a(snmadbg.o)' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
make[1]: *** [/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/nmccollector] Error 1
make: *** [nmccollecto
INFO: r] Error 2

```I'm still looking for a solution...

How did you get to 88%?

---

### Post by dragos2 on 2009-07-24
> **GusPS said:**
> I'm trying this on Jaunty Server 64 bits and I get stuck at 65%. It's in the Linking phase.

```
Error in invoking target 'collector' of makefile '/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/ins_emdb.mk'.
```Previous log:

```
INFO: /ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/snmccolm.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmccol.a(nmccole.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbuf.a(nmcbuft.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g
INFO: /product/10.2.0/db_1/sysman/lib/libnmcbuf.a(nmcbufw.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbuf.a(nmcbufu.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbuf.a(snmcbufm.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/libnmcbu
INFO: f.a(nmcbuff.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib//libnmadbg.a(nmadbg.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `/u01/oracle/10g/product/10.2.0/db_1/sysman/lib//libnmadbg.a(snmadbg.o)' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
make[1]: *** [/u01/oracle/10g/product/10.2.0/db_1/sysman/lib/nmccollector] Error 1
make: *** [nmccollecto
INFO: r] Error 2

```I'm still looking for a solution...

How did you get to 88%?


I installed it by doing Continue on those 2 errros.

It seems that you are installling Oracle 32 bit on 64 bit OS ?

---

### Post by GusPS on 2009-07-27
The file that I'm installing is "10201_database_linux_x86_64.cpio". Are you installing 11g?

I guess those errors can't be skipped. I don't know what the "collector" is needed for, but it's refering the sysman component so that should be important.

I'll be searching for another info. If I can install it, I'll let you know....

---

### Post by GusPS on 2009-07-27
I've found this:

[http://nickhumphrey.net/showthread.php?t=2036](http://nickhumphrey.net/showthread.php?t=2036)

Tomorrow I'll try it.

---

### Post by GusPS on 2009-07-28
Well, it worked.

I just press "continue" on the Link Phase and follow the rest of the instalation without additional errors. Indeed I could run the scripts as root without the error mentioned in the link on previous post.

I'm going to test everything now, because the "collector" error maybe means a future problem.

---

### Post by dizwell on 2009-07-29
For 9.04 and 64-bit Oracle, you could try:

[http://diznix.com/2009/07/27/64-bit-oracle-on-64-bit-ubuntu/](http://diznix.com/2009/07/27/64-bit-oracle-on-64-bit-ubuntu/)

---

### Post by dragos2 on 2009-07-29
For 8.04 32 bit and Oracle 32 bit this guide
[http://www.pythian.com/news/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron](http://www.pythian.com/news/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron)

I installed Oracle 64 bit on Ubuntu Server 64 bit following the upper method but
with few tricks it worked so it can be done on 64 bit too - I think this is pioneering work :))

---

### Post by GusPS on 2009-08-26
Now, I wish to upgrade to 10.2.0.2. Anyone has tried it? Does it works?

---

### Post by dizwell on 2009-09-05
[http://diznix.com/oracle/goal/](http://diznix.com/oracle/goal/)

That's 64-bit Oracle 10g, 11g Release 1 or 11g Release 2 installable on Centos/Redhat, OpenSuse or Ubuntu.

However, it now being September 2009, I consider installing onto Ubuntu 8.10 a bit archaic and therefore the scripts have only been tested to destruction on Ubuntu 9.04. They may work on 8.04, of course, but you're on your own for that one (would be interested to hear the degree of success/failure you have in that case, though).

---

### Post by GusPS on 2009-09-05
Thanks for the link. That's about installing a new Oracle. I've done it right now and it's working ok on Jaunty.
What I want now is to upgrade to 10.2.0.2 (the installation is 10.2.0.1).
The bad thing is that the database is in use, so i'm trying to get a lot of information before doing anyhting, because I don't want to reinstall everything.
Thanks again.

---

### Post by dizwell on 2009-09-06
When you install a new version of Oracle, you get offered the opportunity to upgrade existing databases via the GUI tool. That's why I pointed you at the link: if you can install a new version of Oracle onto Ubuntu, you can perform the upgrade.

I'm slightly confused, though, as to why it's a 'bad thing that the database is in use'. It presumably cannot be a very important database, otherwise you wouldn't be running Oracle on a completely unsupported platform. (Oracle, officially, simply doesn't work on Ubuntu: you really don't want to be running production databases on it).

Similarly, upgrading via patches is something you only do to production databases with the backing of full Oracle support (the patches simply aren't available to anyone without a proper Oracle license). So, at otn.oracle.com, the only free download available for the Linux platform is a 10.2.0.1 one. So how come you are trying to upgrade to 10.2.0.2? That would imply you have patches. But those would only be available if you were running with a support contract. But Oracle won't touch an Ubuntu platform come hell or high water... hence my confusion!

For the record, I installed 10.2.0.1 on Ubuntu and created a database. I then installed 11gR1 and part of that installation prompted me to upgrade the database, which worked flawlessly.

But patching a 10.2.0.1 database to 10.2.0.3: that's a patch, not an upgrade, and those shouldn't even be available given your choice of OS.

If it was me, I would be performing a full database export; wiping everything; installing 11g from scratch; and then performing a full import. I wouldn't be looking for upgrades to work in an environment where getting the installer to work *at all* is something of a miracle, frankly!

---

