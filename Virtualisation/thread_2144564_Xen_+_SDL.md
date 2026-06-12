---
title: "Xen + SDL"
date: 2013-05-12
forum: Virtualisation
---

### Post by Li1t on 2013-05-12
Hi Guys,

I'm trying to get a basic Xen setup using SDL under Ubuntu 13.04 (64-bit). I don't need remote access, I severely dislike the lag and tearing caused by VNC, so I'm trying to get SDL working. I have my virtual machine working and booting under VNC, but whenever I try and enable SDL I get the following error:
```
libxl: error: libxl_dm.c:1212:device_model_spawn_outcome: domain 2 device model: spawn failed (rc=-3)
```
Checking the qemu log file, I can also see this error
```
/usr/lib/xen-4.2/bin/qemu-dm: invalid option -- '-sdl'
```
Now, looking up this error, it seems that the problem is that the version of xen tools that come with Ubuntu have been compiled without support for SDL... I've heard that one solution is to download and recompile Xen tools from source, but I'm in a bit at the deep end here as I've no real experience of compiling from source. Couldn't they just release binaries with SDL support? Would someone with more experience compiling be able to compile and make it into a .deb for me?

I've managed to get it to configure and make up to a point... I had a few errors but was able to resolve them by adding additional packages. I am, however, getting the following error and I just plain don't know how to resolve it:
```
  LINK  i386-softmmu/qemu-system-i386
../slirp/misc.o: In function `memset':
/usr/include/x86_64-linux-gnu/bits/string3.h:81: warning: memset used with constant zero length parameter; this could be due to transposed parameters
/usr/bin/ld: ../qemu-timer.o: undefined reference to symbol 'timer_settime@@GLIBC_2.3.3'
/usr/bin/ld: note: 'timer_settime@@GLIBC_2.3.3' is defined in DSO /lib/x86_64-linux-gnu/librt.so.1 so try adding it to the linker command line
/lib/x86_64-linux-gnu/librt.so.1: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make[1]: *** [qemu-system-i386] Error 1
make: *** [subdir-i386-softmmu] Error 2
```
Now, I realise that this offers me a solution, but I honestly wouldn't know where the linker command line is or how to add something to it. Any ideas short of reading a guide on how to compile under linux? Even if the only solution is to learn to compile using a guide, some direction on what guide to use would be appreciated.

---

### Post by heiko_s on 2013-05-13
I have no experience (yet) with Xen 4.2 and xl, but you could install Ubuntu 12.10 and use Xen 4.1.3 with the xm toolstack (or downgrade your Xen hypervisor and install xend). I've been happy with Xen 4.1 and the xm toolstack so far, though xm is deprecated now.

---

