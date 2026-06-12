---
title: "librt.so linker command line error for g2o package building"
date: 2015-06-09
forum: Ubuntu Application Development
---

### Post by chidanand2 on 2015-06-09
Hai ,

I want to build g2O package using Ubuntu 12.0.4 for ROS based programming.

I stuck with the link error 

[COLOR=#ff0000]/usr/bin/ld: /usr/local/lib/libsuitesparseconfig.a(SuiteSparse_config.o): undefined reference to symbol 'clock_gettime@@GLIBC_2.2'
/usr/bin/ld: note: 'clock_gettime@@GLIBC_2.2' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/librt.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/librt.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [../bin/g2o_incremental] Error 1
make[1]: *** [g2o/examples/interactive_slam/g2o_incremental/CMakeFiles/g2o_incremental_application.dir/all] Error 2
make: *** [all] Error 2[/COLOR]

Any help from anybody will really appreciated.

Regards
Chidanand

---

