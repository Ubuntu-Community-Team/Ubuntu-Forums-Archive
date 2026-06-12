---
title: "Virtualbox DKMS with 3.13rc2 - Not compiling"
date: 2013-11-30
forum: Ubuntu Development Version
---

### Post by rimez on 2013-11-30
Hi all,

In Ubuntu 13.10 I have installed the 3.13rc2 kernel (Ubuntu Mainline). It runs fine except that I get errors with the virtualbox DKMS when installing. As a result I cannot run virtualbox. 

Here's the error I got when installing the kernel (sudo dpkg -i linux-headers-3.13*.deb linux-image-3.13*.deb):
```
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-031300rc2-generic /boot/vmlinuz-3.13.0-031300rc2-generic
Error! Bad return status for module build on kernel: 3.13.0-031300rc2-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.2.16/build/make.log for more information.

```

And here's the log file listing the issue. Unfortuantely I have no idea how to fix this :(
```
DKMS make.log for virtualbox-4.2.16 for kernel 3.13.0-031300rc2-generic (x86_64)
Sat Nov 30 08:22:49 CET 2013
make: Entering directory `/usr/src/linux-headers-3.13.0-031300rc2-generic'
  LD      /var/lib/dkms/virtualbox/4.2.16/build/built-in.o
  LD      /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/linux/SUPDrv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/SUPDrv.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/SUPDrvSem.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/SUPDrvTracer.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/alloc-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/initterm-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/memobj-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/mpnotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/powernotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/assert-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/alloc-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/initterm-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o
/var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c: In function ‘rtR0MemObjNativeMapUser’:
/var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1539:26: error: ‘struct mm_struct’ has no member named ‘numa_next_reset’
                 pTask->mm->numa_next_reset = jiffies + 0x7fffffffffffffffUL;
                          ^
make[2]: *** [/var/lib/dkms/virtualbox/4.2.16/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox/4.2.16/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/virtualbox/4.2.16/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-031300rc2-generic'
```

Does anyone know how I can resolve this? Because I have new hardware, I'm curretly running the Ubuntu mainline kernel 3.12 (without issue). I was really hoping to take advantage of some of the fixes introduced in 3.13 so any help resolving this would be appreciated. 

Also, for what it's worth, I have also tried compiling the kernel myself from the official mainline kernel source but with the same result. Right now of course, I'm just trying to use the Ubuntu mainline builds.

I'm using the Ubuntu package of Virutalbox 4.2.16xxx with the Virtualbox DKMS package installed.

---

### Post by c0h1b4 on 2013-12-02
Hi,

had the same issue. You have to update your virtualbox to 4.3.4.

[http://linuxg.net/how-to-install-virtualbox-4-3-4-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/](http://linuxg.net/how-to-install-virtualbox-4-3-4-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/)

I hope that this fix the issue. Good luck.

---

### Post by rimez on 2013-12-03
@[**[COLOR=#000000]c0h1b4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1742710")

Thanks! That worked!

---

