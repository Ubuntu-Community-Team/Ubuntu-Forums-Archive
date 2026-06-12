---
title: "Compiling VST Server 0.3.1 in Ubuntu Studio 9.04"
date: 2009-09-26
forum: Ubuntu Studio
---

### Post by dead_devil_66 on 2009-09-26
This is the output:

```

deaddevil66@deaddevil66pc:~/vstserver-0.3.1$ sudo make
[sudo] password for deaddevil66: 
echo "\
    cd include/vst;\
    cp ../aeffectx_org.h aeffectx.h;\
    patch -p0 <../aeffectx.diff\
    " >makevstserver.sh
sh makevstserver.sh
patching file aeffectx.h
rm makevstserver.sh
gcc -c server/vstserver.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT  -DVERSION_MAJOR=0 -DVERSION_MINOR=3 -DVERSION_MINOR_MINOR=1
gcc -c library/newdelete.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT  -DVERSION_MAJOR=0 -DVERSION_MINOR=3 -DVERSION_MINOR_MINOR=1
gcc -c library/setparameter.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/getparameter.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/dispatcher.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/process.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/processreplacing.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/processing.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/l_effProcessEvents.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c k_various/k_communicate.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
k_various/k_communicate.c: In function ‘C_newInput’:
k_various/k_communicate.c:144: warning: format not a string literal and no format arguments
k_various/k_communicate.c: In function ‘C_newOutput’:
k_various/k_communicate.c:191: warning: format not a string literal and no format arguments
gcc -c k_various/k_locks.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c common/cache.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
gcc -c library/newdeletecache.c -Wall -Iinclude -Ik_various/include -I/site/include -I/usr/local/include -g -fPIC -D_REENTRANT 
ar rus libvst.a newdelete.o setparameter.o getparameter.o dispatcher.o process.o processreplacing.o processing.o l_effProcessEvents.o k_communicate.o k_locks.o cache.o newdeletecache.o
ar: creating libvst.a
gcc -o vstserver vstserver.o -L. -lvst
echo "\
    cd servant/win;\
    /usr/local/bin/winemaker --lower-none --nolower-include --nosource-fix --nobanner --nobackup -I../../include -I/usr/local/include/wine/windows -L../.. -lvstservant -L/usr/local/lib -L/site/lib .;\
    ./configure  --with-wine=/usr/local\
    " >makevstserver.sh
sh makevstserver.sh
Scanning the source directories...
Generating project files...
  .
makevstserver.sh: 1: ./configure: not found
make: *** [servant/win/Makefile] Error 127

```How can i solve this without the configure file? There isnt any, as far as i can see...

---

### Post by Stochastic on 2009-09-27
Did you install the Ubuntu 9.04 package of wine (and if so, which packages) or did you follow the vstserver install instructions and install the provided version of wine?  (step #1 of the Install file)

---

### Post by dead_devil_66 on 2009-09-28
> **Stochastic said:**
> Did you install the Ubuntu 9.04 package of wine (and if so, which packages) or did you follow the vstserver install instructions and install the provided version of wine?  (step #1 of the Install file)

i tried to compile it but.....when i got to the part that i need to use "make", i got this output:

```

deaddevil66@deaddevil66pc:~/wine$ make
make[1]: Entering directory `/home/deaddevil66/wine/libs'
make[2]: Entering directory `/home/deaddevil66/wine/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/port'
make[2]: Entering directory `/home/deaddevil66/wine/libs/unicode'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/unicode'
make[2]: Entering directory `/home/deaddevil66/wine/libs/uuid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/uuid'
make[2]: Entering directory `/home/deaddevil66/wine/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/wine'
make[2]: Entering directory `/home/deaddevil66/wine/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/wpp'
make[1]: Leaving directory `/home/deaddevil66/wine/libs'
make[1]: Entering directory `/home/deaddevil66/wine/tools'
make[2]: Entering directory `/home/deaddevil66/wine/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/widl'
make[2]: Entering directory `/home/deaddevil66/wine/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winebuild'
make[2]: Entering directory `/home/deaddevil66/wine/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winedump'
make[2]: Entering directory `/home/deaddevil66/wine/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winegcc'
make[2]: Entering directory `/home/deaddevil66/wine/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/wmc'
make[2]: Entering directory `/home/deaddevil66/wine/tools/wrc'
gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/local/include/wine\""  -Wall -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:764: error: lvalue required as increment operand
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:875: error: lvalue required as increment operand
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/deaddevil66/wine/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/deaddevil66/wine/tools'
make: *** [tools] Error 2

```

---

### Post by thorgal on 2009-09-28
mmmm, are you sure this code is not too old ?

in [http://archive.notam02.no/arkiv/src/](http://archive.notam02.no/arkiv/src/)

you can see that the code dates back from early 2004. It would not surprise me that gcc4 cannot compile it.

---

### Post by dead_devil_66 on 2009-09-28
> **thorgal said:**
> mmmm, are you sure this code is not too old ?

in [http://archive.notam02.no/arkiv/src/](http://archive.notam02.no/arkiv/src/)

you can see that the code dates back from early 2004. It would not surprise me that gcc4 cannot compile it.

so how can i compile it? i know it is old....but i need it lol

---

### Post by thorgal on 2009-09-28
ah wait, you're trying to compile wine ...

mmm, I don't see why. Looking at your first post, I can see that the vstserver package is missing a file (./configure in the subdirectory servant/win). Since it cannot find it, the make process fails. It looks like this source package is broken.

By the way, the main makefile has a hardcoded /usr/local for the wine directory. Edit the main makefile so that it contains /usr if you have wine and wine-dev packages installed in /usr

or run

make WINEPATH=/usr to overwrite the /usr/local default of the makefile. It won't help you with the missing configure file though.

---

### Post by dead_devil_66 on 2009-09-28
does any of you know where i can get a clean zip of vstserver? the one in the official arquives is missing one configure file

---

