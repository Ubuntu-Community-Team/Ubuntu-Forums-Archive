---
title: "Re: Installing AC1200 Dual-Band USB 3.0 Wifi Adapter (not A6210)"
date: 2018-12-01
forum: Ubuntu/Debian BASED
---

### Post by glumain on 2018-12-01
Hi,

Please help me with next steps to install my AC1200 Dual-Band USB 3.0 WiFi Adapter. I'm a newbie in Linux. 

I'm getting a problem in the "***sudo dkms build -m rtl88x2bu -v ${VER}***" command. 


root@kali:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044# sudo dkms build -m rtl88x2bu -v ${VER}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j1 KERNELRELEASE=4.18.0-kali2-amd64 KVER=4.18.0-kali2-amd64.....(bad exit status: 2)
Error! Bad return status for module build on kernel: 4.18.0-kali2-amd64 (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.


===============================
Here's the **make.log** but I don't know how to interpret it yet:

DKMS make.log for rtl88x2bu-5.2.4.4 for kernel 4.18.0-kali2-amd64 (x86_64)
Sun Dec  2 12:04:42 +08 2018
/bin/sh: 1: bc: not found
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-kali2-amd64/build M=/var/lib/dkms/rtl88x2bu/5.2.4.4/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-kali2-amd64'
/bin/sh: 1: bc: not found
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.o
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.c: In function ‘dump_drv_version’:
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.c:45:62: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
  RTW_PRINT_SEL(sel, "build time: %s %s\n", __DATE__, __TIME__);
                                                              ^
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.c:45:62: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.c:45:62: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.c:45:62: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
cc1: all warnings being treated as errors
make[4]: *** [/usr/src/linux-headers-4.18.0-kali2-common/scripts/Makefile.build:323: /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.o] Error 1
make[3]: *** [/usr/src/linux-headers-4.18.0-kali2-common/Makefile:1531: _module_/var/lib/dkms/rtl88x2bu/5.2.4.4/build] Error 2
make[2]: *** [Makefile:146: sub-make] Error 2
make[1]: *** [Makefile:8: all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-kali2-amd64'
make: *** [Makefile:1794: modules] Error 2


Thank you in advance for your help.

---

### Post by jeremy31 on 2018-12-02
Split from [https://ubuntuforums.org/showthread.php?t=2394372](https://ubuntuforums.org/showthread.php?t=2394372)

---

