---
title: "Ardour w/VST compiling problems (SCON)"
date: 2011-12-24
forum: Ubuntu Studio
---

### Post by Luke3026 on 2011-12-24
I'm not running Ubuntu Studio, just the generic 11.10, but thought this forum might be the place to post this question.

I've been trying to build Ardour2 w/VST support using the instructions here - [http://ardour.org/building_ardour2](http://ardour.org/building_ardour2)

And after chasing down a number of dependencies, I've hit a wall on the build step.  Here's what the tail end of the output says:

libs/fst/vsti.o: In function `stop_midireceiver':
vsti.c:(.text+0x6b1): undefined reference to `pthread_join'
libs/fst/thread.o: In function `wine_pthread_create':
thread.c:(.text+0x11c): undefined reference to `pthread_attr_getstacksize'
collect2: ld returned 1 exit status
winegcc: i686-linux-gnu-g++ failed
scons: *** [vst/ardour_vst] Error 2
scons: building terminated because of errors.


Not sure where to go from here.  Any ideas?

Thanks!

---

### Post by jejeman on 2011-12-25
Why not use precompiled version from Ardour devs? As I remembre they are encourageing users to use that version.
I think you will be better off posting problem on Ardour forum.

---

