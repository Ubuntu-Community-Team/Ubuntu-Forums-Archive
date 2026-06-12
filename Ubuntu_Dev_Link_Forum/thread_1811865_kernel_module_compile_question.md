---
title: "kernel module compile question"
date: 2011-07-25
forum: Ubuntu Dev Link Forum
---

### Post by dmitttri on 2011-07-25
Hello to everyone,
i have a question regarding compiling and running kernel modules on Kubuntu 10.04.

I have some basic experience on making kernel modules, but i am new to Ubuntu distro. I managed to compile a test kernel module (test.ko) but i got message:
 
  insmod: error inserting 'test.ko': -1 Invalid module format

File /boot/config-2.6.32-24-generic clearly states current kernel version
But modeinfo test.ko says i compiled  [ 2.6.32.41+drm33.18 SMP mod_unload ]

Normally i obtained kernel source kode with:
    apt-get source linux-image-$(uname -r)

So questions are:

1) can i build a kernel module only with headers and lib/modules folder contents
2) can i found a tarball with 2.6.32.24-generic source, or can i download it?

Of course, i am writing this topic after a lot of 'googling' :)

Thanks in advance

---

