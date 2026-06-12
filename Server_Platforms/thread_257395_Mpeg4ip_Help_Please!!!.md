---
title: "Mpeg4ip Help Please!!!"
date: 2006-09-14
forum: Server Platforms
---

### Post by lamadredelsapo on 2006-09-14
I'm trying to install MPEG4IP following the readme instructions but when it comes to execute "make" it gives me the following error:
[INDENT][INDENT]source='bitstream.cpp' object='bitstream.lo' libtool=yes \
        depfile='.deps/bitstream.Plo' tmpdepfile='.deps/bitstream.TPlo' \
        depmode=gcc3 /bin/sh ../../depcomp \
        /bin/sh ../../libtool --mode=compile c++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include   -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Werror -Wmissing-prototypes -Wmissing-declarations -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -g -O2 -DUSE_MMX -DMPEG4IP -c -o bitstream.lo `test -f bitstream.cpp || echo './'`bitstream.cpp
mkdir .libs
c++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Werror -Wmissing-prototypes -Wmissing-declarations -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -g -O2 -DUSE_MMX -DMPEG4IP -c bitstream.cpp -MT bitstream.lo -MD -MP -MF .deps/bitstream.TPlo  -fPIC -DPIC -o .libs/bitstream.lo
cc1plus: warnings being treated as errors
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-declarations" is valid for C/ObjC but not for C++
make[3]: *** [bitstream.lo] Error 1
make[3]: Leaving directory `/home/fernando/mpeg4ip-0.9.8/lib/bitstream'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/fernando/mpeg4ip-0.9.8/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/fernando/mpeg4ip-0.9.8'
make: *** [all] Error 2[/INDENT][/INDENT]

It's quite annoying not to know the real cause. Has anybody managed to install these???

---

