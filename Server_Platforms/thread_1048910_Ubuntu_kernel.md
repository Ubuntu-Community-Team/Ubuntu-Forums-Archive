---
title: "Ubuntu kernel"
date: 2009-01-23
forum: Server Platforms
---

### Post by jairom70 on 2009-01-23
Im tryin to compile kernel. I enter the followin commands						

cd linux-2.6.26.8
make menuconfig

I get error when i enter "make menuconfig" saying :

scripts/Kconfig/mcof arch/x86/Kconfig
lib/Kconfig.debug:663: cant open file "kernel/trace/Kconfig"
make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2

what am i doing wrong?

---

### Post by windependence on 2009-01-24
Why are you recompiling the kernel? Ubuntu uses a modular kernel where you can dynamically load modules if you need additional support in the kernel. 

If you are just doing this to learn, try FreeBSD. Those guys recompile kernels as a matter of daily life. :)

-Tim

---

### Post by linux_tech on 2009-01-24
I'm not sure what commands you ran earlier so check these 2 references 
to see steps to compile and try again 

[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)
[http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

---

