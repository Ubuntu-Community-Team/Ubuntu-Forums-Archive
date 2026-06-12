---
title: "kdenlive install problems"
date: 2008-11-05
forum: Ubuntu Studio
---

### Post by Toadinator on 2008-11-05
I'm trying to compile kdenline 0.7 beta 1 from SVN and I'm getting this after I type in the "make" command:

```
$ make
[  0%] Building CXX object src/cmake_bindir/CMakeFiles/kdenlive.dir/kdenlive_automoc.o
In file included from /home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/moc_initeffects.cpp:10,
                 from /home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/kdenlive_automoc.cpp:9:
/home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/../../../src/initeffects.h:50: error: ISO C++ forbids declaration of ‘Repository’ with no type
/home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/../../../src/initeffects.h:50: error: invalid use of ‘::’
/home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/../../../src/initeffects.h:50: error: expected ‘;’ before ‘*’ token
/home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/../../../src/initeffects.h:51: error: ‘Mlt::Repository’ has not been declared
/home/ryan/Downloads/kdenlivesources/kdenlive/build/src/cmake_bindir/../../../src/initeffects.h:52: error: ‘Mlt::Repository’ has not been declared
make[2]: *** [src/cmake_bindir/CMakeFiles/kdenlive.dir/kdenlive_automoc.o] Error 1
make[1]: *** [src/cmake_bindir/CMakeFiles/kdenlive.dir/all] Error 2
make: *** [all] Error 2

```

What's going wrong?

---

### Post by fregl on 2008-11-14
Your version of mlt and mlt++ are too old. It works here with mlt-0.3.2 from [http://www.mltframework.org/twiki/bin/view/MLT/](http://www.mltframework.org/twiki/bin/view/MLT/)
When compiling mlt make sure you have sox, libsox-dev and libsamplerate0-dev installed.
You also need libsmpeg-dev.

---

