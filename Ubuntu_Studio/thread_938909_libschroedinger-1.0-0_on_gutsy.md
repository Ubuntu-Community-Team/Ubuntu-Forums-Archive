---
title: "libschroedinger-1.0-0 on gutsy"
date: 2008-10-05
forum: Ubuntu Studio
---

### Post by tom_a_sparks on 2008-10-05
can some backport libschroedinger-1.0-0 to gutsy
I have tried to compile libschroedinger-1.0-0 from the source
but it depends on liboil-0.3.13 witch depends on libc6 (>= 2.7-1)
liboil-0.3.13 fails to complie

> make[3]: Entering directory `/home/tom/ffmpeg/schroedinger-1.0.0/liboil-0.3.13/examples/jit'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -Wall -D_BSD_SOURCE -D_GNU_SOURCE -I../.. -DOIL_ENABLE_UNSTABLE_API  -g -O2 -MT jit.o -MD -MP -MF ".deps/jit.Tpo" -c -o jit.o jit.c; \
        then mv -f ".deps/jit.Tpo" ".deps/jit.Po"; else rm -f ".deps/jit.Tpo"; exit 1; fi
jit.c:4:18: error: glib.h: No such file or directory

---

