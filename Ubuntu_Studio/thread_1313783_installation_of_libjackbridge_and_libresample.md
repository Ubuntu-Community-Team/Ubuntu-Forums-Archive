---
title: "installation of libjackbridge and libresample"
date: 2009-11-04
forum: Ubuntu Studio
---

### Post by Vigh on 2009-11-04
Hi i'm having some difficulty install libjackbridge, its missing the dependency libresample, but I having trouble installing that also. Outputs are as follows-


jackbridge
Making install in src
make[1]: Entering directory `/home/anthony/Desktop/libjackbridge-0.3.0/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -g -O2 -MT jackbridge.lo -MD -MP -MF .deps/jackbridge.Tpo -c -o jackbridge.lo jackbridge.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -g -O2 -MT jackbridge.lo -MD -MP -MF .deps/jackbridge.Tpo -c jackbridge.c  -fPIC -DPIC -o .libs/jackbridge.o
jackbridge.c:31:25: error: libresample.h: No such file or directory
jackbridge.c: In function ‘jb_bind’:
jackbridge.c:281: warning: assignment makes pointer from integer without a cast
jackbridge.c: In function ‘jb_set_resampling_quality’:
jackbridge.c:322: warning: assignment makes pointer from integer without a cast
make[1]: *** [jackbridge.lo] Error 1
make[1]: Leaving directory `/home/anthony/Desktop/libjackbridge-0.3.0/src'
make: *** [install-recursive] Error 1

libresample is reporting to have installed correctly so I might try a restart

---

### Post by DemoniacDeath on 2010-12-07
Can anybody help me? I cannot install jackbridge executable. Ubuntu 10.10, x64. I downloaded libjackbridge-0.3.0 source files, installed all needed dependencies (libjack-jackd2-dev and libresample1-dev), then made './configure && make && sudo make install' and it successfully installed libjackbridge, but not a jackbridge binary file. Where can I find this binary and if it should be compiled from this sources why didn't it?
P.S.: Sorry for my bad English

---

### Post by AutoStatic on 2010-12-08
Sorry to ask but for what purpose do you need jackbridge? Maybe there's a better way to achieve what you're after.

Best,

Jeremy

---

### Post by DemoniacDeath on 2010-12-11
I need it to run Reaper under wine with wineasio. I really want to find a way to do this without jackbridge, but I'm stuck

---

### Post by AutoStatic on 2010-12-11
I'm really unfamiliar with those two applications (Wine and Reaper) so can't help you out with that, sorry :(
But afaik you don't need jackbridge when using wineasio. But it has been years last time I used wineasio so I could be wrong. I don't recall ever having used jackbridge though.

Best,

Jeremy

---

### Post by DemoniacDeath on 2010-12-14
As I read somewhere, I need this to use wineasio on my x64 PC. Anyway, does anybody knows where can I find this executable?

---

### Post by Vigh on 2010-12-17
you got an old win xp license? im using all my pro audio on linux using a virtual box now, works a treat, just get ORACLE VirtBox PESU version with usb support, and have a virtual xp in the background for running your audio apps

---

### Post by DemoniacDeath on 2010-12-26
Interesting. What about delay? I'll try it today, maybe this is the solution of my problems :)

---

