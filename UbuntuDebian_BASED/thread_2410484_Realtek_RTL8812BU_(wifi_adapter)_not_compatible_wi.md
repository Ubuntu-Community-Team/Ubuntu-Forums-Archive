---
title: "Realtek RTL8812BU (wifi adapter) not compatible with 18.10 but work with Window 10"
date: 2019-01-16
forum: Ubuntu/Debian BASED
---

### Post by jaime3 on 2019-01-16
Hello guys

I have a Inamax wifi adapter 1200Mbps uses Realtek RTL8812BU. Here is a lsusb can someone help me get it going. I don't want to use the belkin I only get like 10Mbps or so with it. 

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 19d2:0307 ZTE WCDMA Technologies MSM 
Bus 001 Device 007: ID 0bda:b812 Realtek Semiconductor Corp. <------- this is it
Bus 001 Device 003: ID 046d:c247 Logitech, Inc. 
Bus 001 Device 008: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 001 Device 005: ID 1b1c:1b3d Corsair 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[https://www.amazon.com/gp/product/B0773ZPKS2/ref=ppx_yo_dt_b_asin_title_o00__o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0773ZPKS2/ref=ppx_yo_dt_b_asin_title_o00__o00_s00?ie=UTF8&psc=1)
[h=1][/h]

---

### Post by jeremy31 on 2019-01-16
Moved to Networking & wireless

Try ```
sudo apt install git dkms build-essential
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git
sudo dkms add ./rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
sudo dkms install rtl88x2bu/5.3.1
```

Secure Boot will need to be disabled in BIOS
Reboot

---

### Post by cass552 on 2019-05-30
Hi,

I tried that and receive the following 

```
root@kali:~# sudo dkms install rtl88x2bu/5.3.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j2 KERNELRELEASE=4.19.0-kali4-amd64 KVER=4.19.0-kali4-amd64 src=/usr/src/rtl88x2bu-5.3.1........(bad exit status: 2)
Error! Bad return status for module build on kernel: 4.19.0-kali4-amd64 (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.3.1/build/make.log for more information.

```

this is the log 
```

DKMS make.log for rtl88x2bu-5.3.1 for kernel 4.19.0-kali4-amd64 (x86_64)
Thu 30 May 2019 07:42:27 AM EDT
/bin/sh: 1: bc: not found
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.19.0-kali4-amd64/build M=/var/lib/dkms/rtl88x2bu/5.3.1/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.19.0-kali4-amd64'
/bin/sh: 1: bc: not found
  CC [M]  /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_io.o
/usr/src/rtl88x2bu-5.3.1/core/rtw_debug.c: In function ‘dump_drv_version’:
/usr/src/rtl88x2bu-5.3.1/core/rtw_debug.c:45:62: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
  RTW_PRINT_SEL(sel, "build time: %s %s\n", __DATE__, __TIME__);
                                                              ^
/usr/src/rtl88x2bu-5.3.1/core/rtw_debug.c:45:62: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
/usr/src/rtl88x2bu-5.3.1/core/rtw_debug.c:45:62: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
/usr/src/rtl88x2bu-5.3.1/core/rtw_debug.c:45:62: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
  CC [M]  /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_ioctl_set.o
cc1: some warnings being treated as errors
make[4]: *** [/usr/src/linux-headers-4.19.0-kali4-common/scripts/Makefile.build:308: /var/lib/dkms/rtl88x2bu/5.3.1/build/core/rtw_debug.o] Error 1
make[4]: *** Waiting for unfinished jobs....
make[3]: *** [/usr/src/linux-headers-4.19.0-kali4-common/Makefile:1535: _module_/var/lib/dkms/rtl88x2bu/5.3.1/build] Error 2
make[2]: *** [Makefile:146: sub-make] Error 2
make[1]: *** [Makefile:8: all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.19.0-kali4-amd64'
make: *** [Makefile:1999: modules] Error 2
```

---

### Post by jeremy31 on 2019-05-30
Moved to Ubuntu/Debian based as Kali is not Ubuntu

---

### Post by miquel6 on 2019-07-31
Thanks @jeremy31, worked on Ubuntu 19.04 with 5.0.0-21-generic kernel.
My wifi dongle is an Asus AC1300 USB-AC54


> **jeremy31 said:**
> Moved to Networking & wireless

Try ```
sudo apt install git dkms build-essential
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git
sudo dkms add ./rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
sudo dkms install rtl88x2bu/5.3.1
```

Secure Boot will need to be disabled in BIOS
Reboot

---

