---
title: "possible to find kernel with imq?"
date: 2009-12-27
forum: Server Platforms
---

### Post by Simryc on 2009-12-27
Hello,

I am compiling kernel with no luck,
at the end make-kpkg I get .deb 400MB size
I am using [http://ubuntuforums.org/showthread.php?t=1221877](http://ubuntuforums.org/showthread.php?t=1221877)

Is there any kernel with imq compiled?

Why Ubuntu in server edition doesn't have such modules like layer7 imq ipp2p etc...

Simon


EDIT:

I have compiled kernel with imq
it took me:
real    160m52.950s
user    143m26.140s
sys     16m53.340s

why so long? is it my mashine so slow? (Xeon 3GHz)
and it take 7 GB space
what I am doing wrong?

I am just:
tar -xf linux-source.tar.bz2
cp /boot/config-myversion /usr/src/linux/.config
make menuconfig (nothing change)
make-kpkg clean
make-kpkg -initrd --revision=17 kernel_image kernel_headers modules_image

please help me

---

### Post by Saptrans on 2010-01-03
You need to switch off "Compile with debug info" option in config. It's in "Kernel hacking" branch. That's why you got such a big kernel.

---

