---
title: "vmware10.0.1+ubuntu-14.10 shared folder issue"
date: 2014-11-12
forum: Virtualisation
---

### Post by wujinzhong on 2014-11-12
```
root@ubuntu-14:/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only# make 
Using 2.6.x kernel build system.
make -C /lib/modules/3.16.0-23-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
  MODULEBUILDDIR= modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-23-generic'
  CC [M]  /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/message.o
In file included from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/backdoor.h:30:0,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/message.c:54:
/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/vm_assert.h:259:0: warning: "DEPRECATED" redefined
    #define DEPRECATED(_fix) do {} while (0)
 ^
In file included from include/linux/kernel.h:13:0,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/kernelStubs.h:36,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/message.c:45:
include/linux/printk.h:106:0: note: this is the location of the previous definition
 #define DEPRECATED "[Deprecated]: "
 ^
  CC [M]  /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/dir.o
In file included from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfs.h:40:0,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsProto.h:37,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/dir.c:37:
/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/vm_assert.h:259:0: warning: "DEPRECATED" redefined
    #define DEPRECATED(_fix) do {} while (0)
 ^
In file included from include/linux/kernel.h:13:0,
                 from ./arch/x86/include/asm/percpu.h:44,
                 from ./arch/x86/include/asm/preempt.h:5,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/dir.c:29:
include/linux/printk.h:106:0: note: this is the location of the previous definition
 #define DEPRECATED "[Deprecated]: "
 ^
  CC [M]  /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/request.o
In file included from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfs.h:40:0,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsProto.h:37,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/module.h:39,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/request.c:38:
/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/vm_assert.h:259:0: warning: "DEPRECATED" redefined
    #define DEPRECATED(_fix) do {} while (0)
 ^
In file included from include/linux/kernel.h:13:0,
                 from ./arch/x86/include/asm/percpu.h:44,
                 from ./arch/x86/include/asm/current.h:5,
                 from ./arch/x86/include/asm/processor.h:15,
                 from ./arch/x86/include/asm/atomic.h:6,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/request.c:29:
include/linux/printk.h:106:0: note: this is the location of the previous definition
 #define DEPRECATED "[Deprecated]: "
 ^
  CC [M]  /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsUtil.o
In file included from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfs.h:40:0,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsUtil.h:55,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsUtil.c:33:
/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/vm_assert.h:259:0: warning: "DEPRECATED" redefined
    #define DEPRECATED(_fix) do {} while (0)
 ^
In file included from include/linux/kernel.h:13:0,
                 from ./arch/x86/include/asm/percpu.h:44,
                 from ./arch/x86/include/asm/preempt.h:5,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsUtil.h:32,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsUtil.c:33:
include/linux/printk.h:106:0: note: this is the location of the previous definition
 #define DEPRECATED "[Deprecated]: "
 ^
  CC [M]  /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/cpName.o
  CC [M]  /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.o
In file included from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfs.h:40:0,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/hgfsProto.h:37,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/module.h:39,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.c:32:
/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/vm_assert.h:259:0: warning: "DEPRECATED" redefined
    #define DEPRECATED(_fix) do {} while (0)
 ^
In file included from include/linux/kernel.h:13:0,
                 from ./arch/x86/include/asm/percpu.h:44,
                 from ./arch/x86/include/asm/preempt.h:5,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/wait.h:8,
                 from include/linux/fs.h:6,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/./shared/compat_fs.h:22,
                 from /tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.c:29:
include/linux/printk.h:106:0: note: this is the location of the previous definition
 #define DEPRECATED "[Deprecated]: "
 ^
[COLOR=#ff0000]/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.c: In function ‘HgfsReadlink’:[/COLOR]
[COLOR=#ff0000]/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.c:186:10: error: implicit declaration of function ‘vfs_readlink’ [-Werror=implicit-function-declaration][/COLOR]
[COLOR=#ff0000]          error = vfs_readlink(dentry, buffer, buflen, fileName);[/COLOR]
[COLOR=#ff0000]          ^[/COLOR]
[COLOR=#ff0000]cc1: some warnings being treated as errors[/COLOR]
[COLOR=#ff0000]scripts/Makefile.build:257: recipe for target '/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.o' failed[/COLOR]
[COLOR=#ff0000]make[2]: *** [/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only/link.o] Error 1[/COLOR]
[COLOR=#ff0000]Makefile:1345: recipe for target '_module_/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only' failed[/COLOR]
[COLOR=#ff0000]make[1]: *** [_module_/tmp/test/vmware-tools-distrib/lib/modules/source/vmhgfs-only] Error 2[/COLOR]
[COLOR=#ff0000]make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-23-generic'[/COLOR]
[COLOR=#ff0000]Makefile:130: recipe for target 'vmhgfs.ko' failed[/COLOR]
[COLOR=#ff0000]make: *** [vmhgfs.ko] Error 2[/COLOR]
```

---

### Post by slickymaster on 2014-11-12
*Moved to the ***Virtualisation*** sub-forum*

Hi wujinzhong, welcome to the forums.

I've edit your post, adding code tags to it. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

