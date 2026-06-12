---
title: "Linux on a Mobile Phone--LG Voyager"
date: 2010-08-12
forum: The Cafe
---

### Post by admiralspark on 2010-08-12
Hello everyone!
I'm starting a new tinkering project. I just recently upgraded my phone and now have an LG Voyager just sitting around. Tore into it to find out that it has a Qualcomm MSM6550 ARM processor (32 bit, RISC). Now, I've got a few distros that are small enough and have the right drivers to operate on the thing, with only one problem:

Being that its an ARM processor, there's no MBR or way to use Grub. As in, I can put linux on it but it won't start. 

So, any ideas of bootloaders to try on an embedded device or maybe a suggestion of where to look?

Thanks
-Kris

---

### Post by Austin25 on 2010-08-12
Well, you could dump it's firmware, do some probing, and find out how it loads natively, or you could find/write your own firmware that could boot from microSD or such.

---

