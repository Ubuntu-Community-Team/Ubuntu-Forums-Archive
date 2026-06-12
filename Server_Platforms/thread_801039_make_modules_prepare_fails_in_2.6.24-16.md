---
title: "make modules_prepare fails in 2.6.24-16"
date: 2008-05-20
forum: Server Platforms
---

### Post by wyldfury on 2008-05-20
Hi,

I'm trying to compile a module against linux-headers-2.6.24-16-server and getting no where. Below is a quick run down of what I've run and the results. Does anyone have any idea whether this is something I'm doing wrong (and if so, what to do about it) or should I be posting a bug?

Thanks for any help.
Guy

#uname -r
2.6.24-16-server
#make mrproper
#cd /usr/src/linux-headers-2.6.24-16-server
#cp /boot/config-2.6.24-16-server .config
#make modules_prepare
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2

---

