---
title: "Can someone make a deb of Quetoo for me?"
date: 2007-08-04
forum: The Cafe
---

### Post by PrimoTurbo on 2007-08-04
I can't seem to compile it.

[http://jdolan.dyndns.org/trac/wiki/Quetoo](http://jdolan.dyndns.org/trac/wiki/Quetoo)

---

### Post by PrimoTurbo on 2007-08-04
I do ./configure && sudo make install

and I get an error: **config.status: error: cannot find input file: data/ctf/Makefile.in **

---

### Post by urukrama on 2007-08-04
Between './configure' and 'make install' (or 'checkinstall' if you want to be able to remove it through apt/Synaptic), you should do 'make' to create the makefile.

---

### Post by bakegoodz on 2007-08-23
I had this problem until I read this.

Your Quake II game data should reside in $PREFIX/share/quake2.  To specify
an alternate path, use --datadir=/some/path.  A quake2 directory is 
automatically appended to the path you provide.  See ./configure --help for
more information.

So on my computer I put in ./configure --datadir=/usr/local/games/quake2
Where I copied the basq2 files to.

Though I still haven't got it to work I get this message when I run it:
ERROR: Couldn't load pics/colormap.pcx
********************
Error: Error during initialization
I think I'm missing something in my data files, does anyone eles have a "pics" subdirectory in their data files?

---

### Post by obsrv on 2008-09-22
I also want these debs but x64 version :)

---

### Post by obsrv on 2008-09-22
I can't compile it:

```
root@ubuntu:/home/obsrv/quetoo-0.6.1# make
make  all-recursive
make[1]: Entering directory `/home/obsrv/quetoo-0.6.1'
Making all in data
make[2]: Entering directory `/home/obsrv/quetoo-0.6.1/data'
Making all in baseq2
make[3]: Entering directory `/home/obsrv/quetoo-0.6.1/data/baseq2'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/obsrv/quetoo-0.6.1/data/baseq2'
make[3]: Entering directory `/home/obsrv/quetoo-0.6.1/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/obsrv/quetoo-0.6.1/data'
make[2]: Leaving directory `/home/obsrv/quetoo-0.6.1/data'
Making all in src
make[2]: Entering directory `/home/obsrv/quetoo-0.6.1/src'
Making all in .
make[3]: Entering directory `/home/obsrv/quetoo-0.6.1/src'
gcc -DHAVE_CONFIG_H -I. -I..    -pipe  -Wall -Werror   -I/include  -I/include -g -O2 -MT quetoo-sv_world.o -MD -MP -MF .deps/quetoo-sv_world.Tpo -c -o quetoo-sv_world.o `test -f 'sv_world.c' || echo './'`sv_world.c
cc1: warnings being treated as errors
sv_world.c: In function ‘SV_AreaEdicts_r’:
sv_world.c:331: warning: cast from pointer to integer of different size
make[3]: *** [quetoo-sv_world.o] Error 1
make[3]: Leaving directory `/home/obsrv/quetoo-0.6.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/obsrv/quetoo-0.6.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/obsrv/quetoo-0.6.1'
make: *** [all] Error 2
root@ubuntu:/home/obsrv/quetoo-0.6.1#  
```

---

