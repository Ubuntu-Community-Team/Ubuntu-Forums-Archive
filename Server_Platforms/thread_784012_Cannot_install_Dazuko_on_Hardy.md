---
title: "Cannot install Dazuko on Hardy"
date: 2008-05-06
forum: Server Platforms
---

### Post by teamanx on 2008-05-06
Hello. I am trying to install real-time virus protection on my Ubuntu 8.04 file server, by using dazuko. But when I try to install dazuko by compililing the sources, I get the following error:
```
error: capabilities are built-in to the kernel
```
This is the explanation of the error, from dazuko's homepage:
> The Linux Default Capabilities security module has been compiled into the kernel itself rather than as a separate module. The Linux Security Model for Linux 2.6 allows multiple security modules to be loaded, but only when the modules themselves allow others to be loaded. The "capability" module unfortunately does not allow other modules to be loaded. However, Dazuko does allow module "stacking". This means that if Linux Default Capabilities are compiled as a separate module, then Dazuko can be loaded first and "capability" loaded afterwards, allowing both security modules to exist together. 
This means that you will need to build a new kernel with Linux Default Capabilities as a module, rather than built in.

So I must patch and re-compile the kernel if I want to install dazuko. Is it really the only way to get it work? 
If so, why such a good distro as Ubuntu doesn't have the possibility to add such an extended kernel module as dazuko, which is, as of today, the only efective way of getting real-time antivirus protection in Linux?

---

### Post by chrone on 2009-01-25
> **teamanx said:**
> Hello. I am trying to install real-time virus protection on my Ubuntu 8.04 file server, by using dazuko. But when I try to install dazuko by compililing the sources, I get the following error:
```
error: capabilities are built-in to the kernel
```
This is the explanation of the error, from dazuko's homepage:


So I must patch and re-compile the kernel if I want to install dazuko. Is it really the only way to get it work? 
If so, why such a good distro as Ubuntu doesn't have the possibility to add such an extended kernel module as dazuko, which is, as of today, the only efective way of getting real-time antivirus protection in Linux?

still no updates on dazuko on hardy? :(

---

### Post by zolero on 2009-05-06
**Hi there, teamanx & chrone!**

I've bothered for a while with the same problem. Today I was fortunate enough, and got its solution. I thought that it will come in handy if I share it with users community. Therefore here we go! This procedure below compiles Dazuko driver module version 2.3.7 (latest legacy stable) on kernel 2.6.24-24-386 version 2.6.24-24.53 (my mainly used kernel; have three kernels installed).

What I've do:

1.) Unpacked source archive; then I've deleted some code lines from **dazuko-linux.c** as it was instructed by author (John Ogness) itself in this post: [http://www.mail-archive.com/dazuko-help@nongnu.org/msg00170.html ]("http://www.mail-archive.com/dazuko-help@nongnu.org/msg00170.html")

But is needed to delete one more line after these, because there remains an unneeded "**endif**" tag (compiler find it, and sucks because of it). Thus **delete lines 88-94** from there (they referring to 2.4 kernels anyway).

2.) Module wont compile yet. Its output error was:

```
zolero@bluestorm:~/ISO_Files/dazuko-2.3.7$ make
make -C /lib/modules/2.6.24-24-386/build SUBDIRS="/home/zolero/ISO_Files/dazuko-2.3.7" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-386'
  CC [M]  /home/zolero/ISO_Files/dazuko-2.3.7/dazuko_linux.o
/home/zolero/ISO_Files/dazuko-2.3.7/dazuko_linux.c: In function &#8216;dazuko_get_full_filename&#8217;:
/home/zolero/ISO_Files/dazuko-2.3.7/**dazuko_linux.c:907: error: too few arguments to function &#8216;__d_path&#8217;**
make[2]: *** [/home/zolero/ISO_Files/dazuko-2.3.7/dazuko_linux.o] Error 1
make[1]: *** [_module_/home/zolero/ISO_Files/dazuko-2.3.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-386'
make: *** [dummy_rule] Error 2
zolero@bluestorm:~/ISO_Files/dazuko-2.3.7$
```Then find this line in the code:

```
temp = __d_path(xfs->dentry, xfs->vfsmount, root, rootmnt, xfs->buffer, PAGE_SIZE);
```After the first step it must be line 907, as stated by compiler. Remove it, and recompile. The result is a compiled **dazuko.ko** in your source tree. Just go ahead and install it by following the instructions that coming with the package. That's all...

3.) As an end note below is my used configuration command:

```
./configure --mapfile=/boot/System.map-2.6.24-24-386 --devicemajor=254 --enable-event-open --enable-event-close --enable-event-exec --enable-event-unlink --enable-event-rmdir --enable-event-close-modified --enable-trusted --enable-syscalls --disable-local-dpath
```Enjoy and have a nice evening.  \\:D/

---

### Post by mohrizmus on 2009-08-14
:popcorn:
Hi all, 
I'm also have the similar problem on Ubuntu Desktop kernel 2.6.24-24-generic while compiling dazuko 2.3.7 stable( error : invalid module).So I try to delete the line code suggested by zolero (delete lines 88-94 dazuko-linux.c).Then compile them.

```

$ tar xvf dazuko-2.3.7.tar.gz
$ cd dazuko-2.3.7
$ sudo -s
# ./configure --enable-syscalls --mapfile=/boot/System.map-2.6.24-24-generic --disable-local-dpath --disable-chroot-support
checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (cc)
kernel source in /lib/modules/2.6.24-24-generic/source... no
kernel build source in /lib/modules/2.6.24-24-generic/build... yes
kernel source in /lib/modules/2.6.24-24-generic/build... yes
acquiring Linux kernel code configuration... ok
checking if Linux is RSBAC patched... no
checking if devfs is enabled... no
discovered host system... Linux (2.6.24)
checking for System.map file... ok (/boot/System.map-2.6.24-24-generic)
locating sys_call_table... ok (0xc0326500)
checking sys_call_table status... read-only

IMPORTANT NOTE:
If you get a kernel panic or segmentation fault while loading
the Dazuko module, you will need to reboot and try to
configure Dazuko again with the --sct-readonly option.

locating do_execve... ok (0xc0197790)
identifying device API... ok
inspecting class type... ok (class)
inspecting nameidata type... ok (path)
inspecting suspend function... ok (suspend2)
inspecting task_struct structure... ok (using parent)
configure: creating Makefile
configure: creating library/Makefile
configure: creating example_c/Makefile

./configure successful

=======================
 Configuration summary
=======================

module events = ON_OPEN ON_CLOSE ON_EXEC
devfs support = no
rsbac support = no
hooking via syscalls = yes
local __d_path() = no (using chroot events, see README.linux26)
path resolution = registered daemon context
module debug = no
library 1.x compatibility = yes

# make
make -C /lib/modules/2.6.24-24-generic/build SUBDIRS="/home/mohdrizal/Desktop/dazuko-2.3.7" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /home/mohdrizal/Desktop/dazuko-2.3.7/dazuko_core.o
  CC [M]  /home/mohdrizal/Desktop/dazuko-2.3.7/dazuko_transport.o
  CC [M]  /home/mohdrizal/Desktop/dazuko-2.3.7/dazuko_linux.o
  LD [M]  /home/mohdrizal/Desktop/dazuko-2.3.7/dazuko.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mohdrizal/Desktop/dazuko-2.3.7/dazuko.mod.o
  LD [M]  /home/mohdrizal/Desktop/dazuko-2.3.7/dazuko.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
touch dummy_rule

# make test
/sbin/insmod ./dazuko.ko
make: *** [test] Segmentation fault

```

I reboot and configure with --sct-readonly to resolve the segmentation fault.I type the code 'make','make test' and 'make install' but give the segmentation error as above.

**But I didn't reboot **,and reconfigure with the --sct-readonly option and compile untill finish.
```

# ./configure --enable-syscalls --mapfile=/boot/System.map-2.6.24-24-generic --disable-local-dpath --disable-chroot-support --sct-readonly
# make
make: `dummy_rule' is up to date.
# make test
/sbin/insmod ./dazuko.ko
insmod: error inserting './dazuko.ko': -1 File exists
make: *** [test] Error 1
# make install
mkdir -p /lib/modules/2.6.24-24-generic/extra
cp dazuko.ko /lib/modules/2.6.24-24-generic/extra
/sbin/depmod -ae

```

Check whether dazuko module is install succesfully.
```

lsmod |grep dazuko

```

It make me happy to compile dazuko 2.3.7 on kernel 2.6.24-24-generic.I have no problem to compile on kernel 2.6.24-49-generic.DazukoFS could be installed automatically on Hardy Heron using Avira Antivir Unix Personel 3.0.x.Thank you zolero to give invaluable resource to solve my problem.

---

