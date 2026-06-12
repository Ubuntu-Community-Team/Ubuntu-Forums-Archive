---
title: "building gtkmm-3-22 on ubuntu with jhbuild (issues)"
date: 2018-04-08
forum: Ubuntu Dev Link Forum
---

### Post by ankebut on 2018-04-08
I have been trying to build gtkmm-3-22 with jhbuild. i did everything before building gtkmm (i.e: jhbuild sysdep bootstrap sanitycheck etc) so now, i come acrros an error:

```
    > make[2]: *** No rule to make target 'desktopappinfo.cc', needed by
    > 'desktopappinfo.lo'.  Stop. make[2]: *** Waiting for unfinished
    > jobs....   CXX      zlibcompressor.lo make[2]: Leaving directory
    > '/home/mdr/jhbuild/checkout/glibmm/gio/giomm' Makefile:711: recipe for
    > target 'all-recursive' failed make[1]: *** [all-recursive] Error 1
    > make[1]: Leaving directory '/home/mdr/jhbuild/checkout/glibmm'
    > Makefile:507: recipe for target 'all' failed make: *** [all] Error 2
    > *** Error during phase build of glibmm: ########## Error running make -j 2  *** [9/23]
    > 
    >   [1] Rerun phase build   [2] Ignore error and continue to install  
    > [3] Give up on module   [4] Start shell   [5] Reload configuration  
    > [6] Go to phase "wipe directory and start over"   [7] Go to phase
    > "configure"   [8] Go to phase "clean"   [9] Go to phase "distclean"
    > choice:
```

full log: [https://pastebin.com/UTGJzHjy](https://pastebin.com/UTGJzHjy)

can you help me please?
best regards.

---

