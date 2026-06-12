---
title: "linux-image-2.6.20-6-ps3, Repository?"
date: 2007-02-11
forum: Repositories &amp; Backports
---

### Post by 3vi1 on 2007-02-11
Can anyone tell me what repo I might add to find the above mentioned package?

I've upgraded my Playstation 3 to Kubuntu Feisty Herd 3, but I'm still using the gentoo 2.6.16-ps3 kernel to make things work.  I saw the above and linux-headers-2.6.20-6-ps3 referenced by packages in my list, but they don't seem to be available in any of the repositories I have configured.

I'm downloading the 2.6.20 source package now, and will try recompiling the kernel myself, assuming they contain everything needed for PS3 support.

-J

---

### Post by 3vi1 on 2007-02-11
I've run into a problem recompiling using the current source... so it looks like I'm stumped until there's an update or I can find the repository with the pre-built images.

...
  LD      init/built-in.o
  LD      .tmp_vmlinux1
arch/powerpc/platforms/built-in.o: In function `.dump_fir':
ras.c:(.text+0x8ad4): undefined reference to `.cbe_get_cpu_pmd_regs'
ras.c:(.text+0x8ae4): undefined reference to `.cbe_get_cpu_iic_regs'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

-J

---

### Post by 3vi1 on 2007-02-12
Nevermind this thread.  I got the kernel to compile (though it's not working 100% right yet).

Also, I updated my source list via source-o-matic (feisty) and was at least able to get the 20-7 image... though the ps3 metapackages don't seem to have been updated at this time.

Unfortunately, the 20-7 kernel fails to mount root for some reason, so I'm using Gentoo's vmlinux on my otherwise Feisty PS3 installation.  I'm not sure if this is a side-effect of kboot or what, yet.

---

### Post by joel1234567 on 2007-03-03
Did you ever get this recompiled kernel working? I am trying to recompile the original kernel source on the ps3 with a few modified settings, but am not having much luck getting it to run. Was wondering if maybe there were some parameters that needed tweaking somewhere.

---

### Post by Ciego on 2007-03-16
Here is a related article that may shed some light on the subject.

[http://julipedia.blogspot.com/2007/03/building-updated-kernel-for-ps3.html](http://julipedia.blogspot.com/2007/03/building-updated-kernel-for-ps3.html)

---

