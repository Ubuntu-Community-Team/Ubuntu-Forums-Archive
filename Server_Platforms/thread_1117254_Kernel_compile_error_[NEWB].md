---
title: "Kernel compile error [NEWB]"
date: 2009-04-05
forum: Server Platforms
---

### Post by doggy93 on 2009-04-05
Hi, I'm pretty new to Linux so I might seem kind of stupid. I'm using Ubuntu Server, and here's my problem.

When I installed Ubuntu Server it came with the 2.6.24-23-server kernel. But I wanted to have a 1000hz kernel for my HLDS Gameserver. So I found the [Kernel Master Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=Master+Kernel+Thread"), and went ahead with step 1. 

Everything went fine untill step 10. Where I was supposed to put in "make-kpkg clean". I got some errors which I solved pretty quickly (Google ftw). I had to add in "--arch=amd64" for it to work as it couldn't find "arch/xen/Makefile". 

Then I went on with the second part. I put in "CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=386 --arch=amd64 kernel_image kernel_headers modules_image" and pressed enter. 

It all went fine all the way until here:

```
This is kernel package version 11.001.
====== making target CONFIG/linux-source-.. [new prereqs: CONFIG-indep]======

====== making target CONFIG/linux-doc-.. [new prereqs: CONFIG-indep]======

====== making target CONFIG/linux-manual-.. [new prereqs: CONFIG-indep]======

====== making stamp-configure-indep because of  ======
====== making target configure-indep [new prereqs: stamp-configure-indep]======
====== making stamp-configure because of  ======
The changelog says we are creating ..
However, I thought the version is 2.6.28.8
exit 4
make: *** [sanity_check] Error 4

```

So this is what I need help for. What to do to make this kernel work?

Thanks in advance,
DoGGy.

---

### Post by doggy93 on 2009-04-05
I got past that little error now, but of course a new error showed up...

```
/usr/src/linux-2.6.28/arch/x86/include/asm/page_64.h:46:2: error: #error "CONFIG_PHYSICAL_START must be a multiple of 2MB"
make[2]: *** [arch/x86/kernel/asm-offsets.s] Error 1
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.28'
make: *** [debian/stamp-build-kernel] Error 2

```

What do I have to do with CONFIG_PHYSICAL? What do I have to set it to?
Or do I even have to set it to anything else? I'm absolutely clueless. Help is apprecciated!!!

---

### Post by doggy93 on 2009-04-06
Solved.

---

