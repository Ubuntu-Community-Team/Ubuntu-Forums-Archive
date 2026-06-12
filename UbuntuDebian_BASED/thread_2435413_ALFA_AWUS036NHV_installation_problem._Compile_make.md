---
title: "ALFA AWUS036NHV installation problem. Compile make driver error: 2 Please check error"
date: 2020-01-20
forum: Ubuntu/Debian BASED
---

### Post by linukhkali on 2020-01-20
Hello, i'm tottaly newbie, and also sorry for my english. 
My system:

lsb_release -a
No LSB modules are available.
Distributor ID: Kali
Description:    Kali GNU/Linux Rolling
Release:        2019.4
Codename:       kali-rolling

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev ff)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

I' m trying install awus036nhv from Alfa pages to my new ALFA usb wireless adapter. During installation have errors:

root@kali:~/Desktop/rt# sh ./install.sh
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
rtl8188EUS_linux_v4.3.0.8_13968.20150417
Authentication requested [root] for make clean:
./install.sh: 39: [: unexpected operator
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
./install.sh: 49: [: unexpected operator
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.3.0-kali2-amd64/build M=/root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417  modules
make[1]: Entering directory '/usr/src/linux-headers-5.3.0-kali2-amd64'
  CC [M]  /root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/core/rtw_cmd.o
In file included from /root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/include/osdep_service.h:41,
                 from /root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/include/drv_types.h:32,
                 from /root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/core/rtw_cmd.c:22:
/root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/include/osdep_service_linux.h: In function ‘_init_timer’:
/root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/include/osdep_service_linux.h:261:8: error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
  261 |  ptimer->data = (unsigned long)cntx;
      |        ^~
/root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/include/osdep_service_linux.h:262:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  262 |  init_timer(ptimer);
      |  ^~~~~~~~~~
      |  _init_timer
cc1: some warnings being treated as errors
make[3]: *** [/usr/src/linux-headers-5.3.0-kali2-common/scripts/Makefile.build:286: /root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417/core/rtw_cmd.o] Error 1
make[2]: *** [/usr/src/linux-headers-5.3.0-kali2-common/Makefile:1639: _module_/root/Desktop/rt/driver/rtl8188EUS_linux_v4.3.0.8_13968.20150417] Error 2
make[1]: *** [/usr/src/linux-headers-5.3.0-kali2-common/Makefile:179: sub-make] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.3.0-kali2-amd64'
make: *** [Makefile:1354: modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

Any help??

---

### Post by coffeecat on 2020-01-20
Kali is not Ubuntu, and is based on Debian, not Ubuntu.

*Thread moved to the **Ubuntu/Debian Based** sub-forum.*

@linukhkali, you describe yourself as a "tottaly newbie" yet you have chosen a difficult distro. You may wish to read Kali Linux's own "Should I Use Kali Linux?" page - [https://www.kali.org/docs/introduction/should-i-use-kali-linux/](https://www.kali.org/docs/introduction/should-i-use-kali-linux/)

A couple of excerpts for you to think about:

> As the distribution’s developers, you might expect us to recommend that everyone should be using Kali Linux. The fact of the matter is, however, that Kali is a Linux distribution specifically geared towards professional penetration testers and security specialists, and given its unique nature, it is **NOT** a recommended distribution if you’re unfamiliar with Linux or are looking for a general-purpose Linux desktop distribution for development, web design, gaming, etc.

> If you are unfamiliar with Linux generally, if you do not have at least a basic level of competence in administering a system, if you are looking for a Linux distribution to use as a learning tool to get to know your way around Linux, or if you want a distro that you can use as a general purpose desktop installation, *Kali Linux is probably not what you are looking for.*

---

### Post by linukhkali on 2020-01-20
Yes, i realize that kali is for professjonals but want to try for now. Propably i will give up and install different distro but if somewone would help mi with my issue i'll be gratefoul :)

---

### Post by wolftrax on 2020-01-20
kali is intended to be run as a live DVD and not installed as a everday OS.  you can install it on a virtual machine but its a pen testing distro and should not be used as a everyday OS and not really a good idea so install as a primary OS on your hard disc.

---

### Post by chili555 on 2020-01-21
Please run and post:

```
lsusb
```What is not working about the Intel device?

---

