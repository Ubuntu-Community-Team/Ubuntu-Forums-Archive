---
title: "Error using make menuconfig"
date: 2016-11-17
forum: Server Platforms
---

### Post by sykay on 2016-11-17
So, I just downloaded the kernel and tried to use make menuconfig command.
This is what I'm getting:

  HOSTCC  scripts/kconfig/mconf.o
In file included from scripts/kconfig/mconf.c:23:0:
scripts/kconfig/lxdialog/dialog.h:38:20: fatal error: curses.h: No such file or directory
compilation terminated.
scripts/Makefile.host:124: recipe for target 'scripts/kconfig/mconf.o' failed
make[1]: *** [scripts/kconfig/mconf.o] Error 1
Makefile:545: recipe for target 'menuconfig' failed
make: *** [menuconfig] Error 2


So, any reasons and solutions for this error?

---

