---
title: "running a file from library..."
date: 2006-10-06
forum: Repositories &amp; Backports
---

### Post by vanth13 on 2006-10-06
I'm trying to use a vision library. I serched for the dependancy list:
    * dependency list (ldd):


        libGLU.so.1 => /usr/lib/libGLU.so.1
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1
        libXmu.so.6 => /usr/X11R6/lib/libXmu.so.6
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6
        libstdc++.so.6 => /usr/lib/libstdc++.so.6
        libm.so.6 => /lib/tls/libm.so.6
        libgcc_s.so.1 => /lib/libgcc_s.so.1
        libc.so.6 => /lib/tls/libc.so.6
        libtiff.so.3 => /usr/lib/libtiff.so.3
        libjpeg.so.62 => /usr/lib/libjpeg.so.62
        libz.so.1 => /usr/lib/libz.so.1
        libthread.so.0 => /usr/lib/libthread.so.0
        libdl.so.2 => /lib/libdl.so.2
        libXt.so.6 => /usr/X11R6/lib/libXt.so.6
        libSM.so.6 => /usr/X11R6/lib/libSM.so.6
        libICE.so.6 => /usr/X11R6/lib/libICE.so.6
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2

but I can't find a lot of them on synaptic. any clue? I'm a new user sorry for the silly question.

this is the error I have running the exmaple:

ucaubu@lucaubu:~/Desktop/visual hull algo/sw/franco/EPVH-1.0/Example$ ./RUN_ME
../reconstruct: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

I've done:

export LD_LIBRARY_PATH= ...location of the library in ...



please help!! it's important for my thesis and I have few time...

---

