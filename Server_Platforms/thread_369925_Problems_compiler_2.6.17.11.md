---
title: "Problems compiler 2.6.17.11"
date: 2007-02-25
forum: Server Platforms
---

### Post by Hypner on 2007-02-25
Hello

I am trying to compile a new kernel or my new ubunto server. I used the old config files that comes with the installation but i doesnt work. It comiles for a while then end up with this error

```
root@ubuntu:/usr/src/linux-2.6.17.11# make all
  CHK     include/linux/version.h
  CHK     include/linux/compile.h
include/asm/byteorder.h:5:28: error: linux/compiler.h: No such file or directory
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x5e3): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x8cb): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0xa81): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xd17): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x43d3): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x4db6): more undefined references to `__stack_chk_fail' follow
make: *** [.tmp_vmlinux1] Error 1

```

---

