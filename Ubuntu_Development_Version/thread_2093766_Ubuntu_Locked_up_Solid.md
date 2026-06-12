---
title: "Ubuntu Locked up Solid"
date: 2012-12-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-12-11
I downloaded and installed the kernel:final and now that install will only load up lightdm with users, blinking cursor, but mouse won't move and cannot get to terminal in the standard manner but GRub Recovery mode is working. Also tried various kernel non rc.

---

### Post by ventrical on 2012-12-11
After installing the latest kernel  it broke xorg and some other depends. I was able to boot into 3.5.n-n and recover this system.

sudo apt-get upgrade -f

Now to track down what happened to that missing kernel. :) lol

---

### Post by ventrical on 2012-12-12
Synaptic installed the 3.7.0-6.14 kernelk. All is back to normal now:

Just a side note on ubuntu resilience: More and more I am able to learn how to recover seemingly unrecoverable linux-ubuntu installs.  This last episode (where I though all was lost) proved again to be a wrong assumption.  All the 3.7  kernels failed. I had to  use a 3.5 version kernel to be able to get to terminal. Once there , in terminal, I was able to recover ubuntu. So even when grub-recovery fails , there always seems to be other methods of  recovery.

  It was not the 3.7 kernels that were bad , but , I assume, that  the way I installed the kernel.final 3.7.0-6.14 from the *.deb packages. xorg and abi13 reportedly 'broke' in the process and were fixed with the -f option after getting to terminal.

---

### Post by grahammechanical on 2012-12-12
I do not have the education to install kernels they way you have done it but looking through Synaptic's filter under kernels, I see something called linux-signed-generic. It is described as "This package will always depend on the latest complete generic Linux kernel and headers. Signed with the Ubuntu EFI key."

It is not installed on my system. But I do not have a motherboard with secure boot. Will this mean complications for those who manually install kernels when testing on secure boot hardware?

Regards.

---

### Post by ventrical on 2012-12-12
> **grahammechanical said:**
> I do not have the education to install kernels they way you have done it but looking through Synaptic's filter under kernels, I see something called linux-signed-generic. It is described as "This package will always depend on the latest complete generic Linux kernel and headers. Signed with the Ubuntu EFI key."

It is not installed on my system. But I do not have a motherboard with secure boot. Will this mean complications for those who manually install kernels when testing on secure boot hardware?

Regards.

Good question . I was just discussing today about purchasing a souped-up Phenom i7 or whatever .. but then ... I just appreciate the way the older machines work ..

---

