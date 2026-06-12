---
title: "Compiling kernel from scratch"
date: 2015-08-29
forum: Ubuntu/Debian BASED
---

### Post by countcobolt on 2015-08-29
Hi all,

I seem to be in a bit of an odd place here. I am trying to build a monolithical (but with module support) kernel for my kodibuntu system, yet for some reason the system gets stuck at loading initramfs. Next it does absolutely nothing. In recovery mode, it does exactly the same thing. The main reason is that I know my hardware (atleast I thought so) and the 26MB initrd is a bit over the top, right? I was used to compiling 2.2 , 2.4 and 2.6 kernel but with the new ones I seem to be in a pickle.

I am now building the new 3.18.20 kernel with the old config from the stock system, hoping this will work, but again it would result back into the massive initrd. What is really safe to remove? What modules are needed to read UUID disks (I am coming from a /dev/sdxxxx system in the past)

Any pointers can help

Kind regards

Steve

---

### Post by howefield on 2015-08-29
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

