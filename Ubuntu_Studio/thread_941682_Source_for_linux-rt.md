---
title: "Source for linux-rt"
date: 2008-10-08
forum: Ubuntu Studio
---

### Post by freke85 on 2008-10-08
Hi all,

I'm searching for the source of linux-image-2.6.24-19-rt.

I know that it is provided by the linux-meta-package and therefore should be part of linux-source, but I actually tried it and the resulting kernel was no rt-kernel (bad latency).

What I did:

apt-get install linux-source
cd /usr/src
tar jxf linux*
cd linux*
cp /boot/config-*rt ./.config
make oldconfig
make-kpkg --initrd --revision=0 kernel_image 
cd ..
dpkg -i *.deb
reboot


Normally, there should be a file called drivers/char/lpptest.c in the rt-patched linux source tree. I can't find it in the source provided by the linux-source-package.

How can I get the source tree of the ubuntu rt-kernel?

Thanks a lot for your help,

freke85

---

### Post by freke85 on 2008-10-08
sorry, I forgot to mention:

I'm using Ubuntu 8.04.1 server (i386).

---

### Post by Stochastic on 2008-10-08
The easiest way is to download it from: [http://packages.ubuntu.com/hardy/linux-rt](http://packages.ubuntu.com/hardy/linux-rt) (over on the right hand side of the page)

---

### Post by freke85 on 2008-10-08
thanks, but this is the source of the meta-package - that's just a debian-package with lots of dependencies.

i downloaded the kernel source from there, too - but still, i can't find any applied rt-patches :-(

---

### Post by Stochastic on 2008-10-09
if you stumble down the rabbit hole of packages (it's only like three steps), you'll soon come across this page: [http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-rt](http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-rt) where I should have sent you originally.  I didn't take any read through the source code looking for the realtime patch, but you may also find it located in parts of the linux-rt-modules package, or other scattered locations - if you're on a serious journey - but I'm no kernel dev, so I don't know.

---

### Post by eye208 on 2008-10-09
> **freke85 said:**
> i downloaded the kernel source from there, too - but still, i can't find any applied rt-patches :-(
There are no separate patches any more. RT capability has become part of the mainline kernel. All you need to do is configure it (make menuconfig etc.) before compiling.

---

### Post by markbuntu on 2008-10-09
linux-rt kernel is in Synaptic, I just looked. rt images are available for the -16 to-21 kernels. For 19:

linux-image-2.6.24-19-rt

---

### Post by freke85 on 2008-10-10
> **eye208 said:**
> There are no separate patches any more. RT capability has become part of the mainline kernel. All you need to do is configure it (make menuconfig etc.) before compiling.

thanks to all of you, I downloaded a vanilla kernel from kernel.org and applied Ingos patch manually.

---

### Post by Stochastic on 2008-10-10
> **freke85 said:**
> thanks to all of you, I downloaded a vanilla kernel from kernel.org and applied Ingos patch manually.

Out of curiosity, why do this manually?

---

