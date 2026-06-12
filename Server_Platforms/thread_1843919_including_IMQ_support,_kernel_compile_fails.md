---
title: "including IMQ support, kernel compile fails"
date: 2011-09-14
forum: Server Platforms
---

### Post by metalfan_ on 2011-09-14
IMPORTANT: IMQ was replaced be IFB. IFB is included in the default ubuntu kernel.
if youre still interrested in howto compile your own kernel with a patch read the second post. it shows the solution
-----------------------------------

hi,

i would like to play around with IMQ [http://www.linuximq.net](http://www.linuximq.net).
for this the kernel needs a patch, this is what i did:

```

apt-get source linux-image-$(uname -r)
cd linux-2.6.38/

patch -p1 <../linux-2.6.38-imq-multiqueue-test1.patch
patching file drivers/net/imq.c
patching file drivers/net/Kconfig
patching file drivers/net/Makefile
patching file include/linux/imq.h
patching file include/linux/netfilter/xt_IMQ.h
patching file include/linux/netfilter.h
patching file include/linux/netfilter_ipv4/ipt_IMQ.h
patching file include/linux/netfilter_ipv6/ip6t_IMQ.h
patching file include/linux/skbuff.h
patching file include/net/netfilter/nf_queue.h
patching file net/core/dev.c
Hunk #2 succeeded at 2085 (offset 2 lines).
Hunk #3 succeeded at 2256 (offset 2 lines).
patching file net/core/skbuff.c
patching file net/ipv4/netfilter/iptable_mangle.c
patching file net/netfilter/core.c
patching file net/netfilter/Kconfig
patching file net/netfilter/Makefile
patching file net/netfilter/nf_internals.h
patching file net/netfilter/nf_queue.c
patching file net/netfilter/xt_IMQ.c


fakeroot debian/rules clean 
<output not included, no errors>


AUTOBUILD=1 fakeroot debian/rules binary-debs
<this runs CC for some time, then asks me two questions about IMQ and finishes with this:>

# configuration written to .config
#
  Using /home/dmkcrew/tmp/kernel/linux-2.6.38 as source for kernel
  /home/dmkcrew/tmp/kernel/linux-2.6.38 is not clean, please run 'make mrproper'
  in the '/home/dmkcrew/tmp/kernel/linux-2.6.38' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/dmkcrew/tmp/kernel/linux-2.6.38'
make: *** [/home/dmkcrew/tmp/kernel/linux-2.6.38/debian/stamps/stamp-prepare-tree-generic] Error 2

```


why does it fail?

i followed this howto:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by metalfan_ on 2011-09-14
This is what fixed the problem, run this right after the patch is applied.
```

cd linx-2.6...
chmod -R +x debian/scripts/ &&  debian/rules updateconfigs

fakeroot make-kpkg --initrd --append-to-version=-lockard kernel-image kernel-headers

```

---

