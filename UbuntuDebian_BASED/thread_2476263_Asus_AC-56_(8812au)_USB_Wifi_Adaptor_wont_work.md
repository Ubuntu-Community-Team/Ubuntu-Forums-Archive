---
title: "Asus AC-56 (8812au) USB Wifi Adaptor wont work"
date: 2022-06-21
forum: Ubuntu/Debian BASED
---

### Post by supercar55uk on 2022-06-21
To cut a long story short, I had to reinstall Zorin Core (I know its not ubuntu but pretty much is. Thought I'd ask here anyway). When I first installed it back at late last year, I had issues getting my Asus AC-56 (8812AU) USB Wifi dongle to work. But I managed to get it working somehow.

 
 
   
 
 
 I have tried installing drivers from github but keep getting this error when I make the install:
 
 
 
 
 [SIZE=2]*steve@PC:~/Downloads/rtl8812au-master$ make*[/SIZE]
 [SIZE=2]*make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.13.0-51-generic/build M=/home/steve/Downloads/rtl8812au-master  modules*[/SIZE]
 [SIZE=2]*make[1]: Entering directory '/usr/src/linux-headers-5.13.0-51-generic'*[/SIZE]
   [SIZE=2]*CC [M]  /home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.o*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c: In function ‘isFileReadable’:*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2096:11: error: implicit declaration of function ‘get_fs’; did you mean ‘get_ds’? [-Werror=implicit-function-declaration]*[/SIZE]
  [SIZE=2]*2096 |   oldfs = get_fs();*[/SIZE]
       [SIZE=2]*|           ^~~~~~*[/SIZE]
       [SIZE=2]*|           get_ds*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2096:11: error: incompatible types when assigning to type ‘mm_segment_t’ {aka ‘struct <anonymous>’} from type ‘int’*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2097:3: error: implicit declaration of function ‘set_fs’; did you mean ‘sget_fc’? [-Werror=implicit-function-declaration]*[/SIZE]
  [SIZE=2]*2097 |   set_fs(get_ds());*[/SIZE]
       [SIZE=2]*|   ^~~~~~*[/SIZE]
       [SIZE=2]*|   sget_fc*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2076:21: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?*[/SIZE]
  [SIZE=2]*2076 |   #define get_ds() (KERNEL_DS)*[/SIZE]
       [SIZE=2]*|                     ^~~~~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2097:10: note: in expansion of macro ‘get_ds’*[/SIZE]
  [SIZE=2]*2097 |   set_fs(get_ds());*[/SIZE]
       [SIZE=2]*|          ^~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2076:21: note: each undeclared identifier is reported only once for each function it appears in*[/SIZE]
  [SIZE=2]*2076 |   #define get_ds() (KERNEL_DS)*[/SIZE]
       [SIZE=2]*|                     ^~~~~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2097:10: note: in expansion of macro ‘get_ds’*[/SIZE]
  [SIZE=2]*2097 |   set_fs(get_ds());*[/SIZE]
       [SIZE=2]*|          ^~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c: In function ‘retriveFromFile’:*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2134:12: error: incompatible types when assigning to type ‘mm_segment_t’ {aka ‘struct <anonymous>’} from type ‘int’*[/SIZE]
  [SIZE=2]*2134 |    oldfs = get_fs();*[/SIZE]
       [SIZE=2]*|            ^~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2076:21: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?*[/SIZE]
  [SIZE=2]*2076 |   #define get_ds() (KERNEL_DS)*[/SIZE]
       [SIZE=2]*|                     ^~~~~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2135:11: note: in expansion of macro ‘get_ds’*[/SIZE]
  [SIZE=2]*2135 |    set_fs(get_ds());*[/SIZE]
       [SIZE=2]*|           ^~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c: In function ‘storeToFile’:*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2169:12: error: incompatible types when assigning to type ‘mm_segment_t’ {aka ‘struct <anonymous>’} from type ‘int’*[/SIZE]
  [SIZE=2]*2169 |    oldfs = get_fs();*[/SIZE]
       [SIZE=2]*|            ^~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2076:21: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?*[/SIZE]
  [SIZE=2]*2076 |   #define get_ds() (KERNEL_DS)*[/SIZE]
       [SIZE=2]*|                     ^~~~~~~~~*[/SIZE]
 [SIZE=2]*/home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.c:2170:11: note: in expansion of macro ‘get_ds’*[/SIZE]
  [SIZE=2]*2170 |    set_fs(get_ds());*[/SIZE]
       [SIZE=2]*|           ^~~~~~*[/SIZE]
 [SIZE=2]*cc1: some warnings being treated as errors*[/SIZE]
 [SIZE=2]*make[2]: *** [scripts/Makefile.build:281: /home/steve/Downloads/rtl8812au-master/os_dep/osdep_service.o] Error 1*[/SIZE]
 [SIZE=2]*make[1]: *** [Makefile:1879: /home/steve/Downloads/rtl8812au-master] Error 2*[/SIZE]
 [SIZE=2]*make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-51-generic'*[/SIZE]
 [SIZE=2]*make: *** [Makefile:1852: modules] Error 2*[/SIZE]
 
 
 
 
 Any ideas why?
 
 
 Also, when I do lsusb I can see the USB adaptor:
 
 
 [SIZE=2]*steve@PC:~/Downloads/rtl8812au-master$ lsusb*[/SIZE]
 [SIZE=2]*Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub*[/SIZE]
 [SIZE=2]*Bus 005 Device 003: ID 0b05:17d2 ASUSTek Computer, Inc. USB-AC56 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU]*[/SIZE]
 [SIZE=2]*Bus 005 Device 002: ID 044f:b106 ThrustMaster, Inc. T.Flight Stick X*[/SIZE]
 [SIZE=2]*Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/SIZE]
 [SIZE=2]*Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub*[/SIZE]
 [SIZE=2]*Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/SIZE]
 [SIZE=2]*Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub*[/SIZE]
 [SIZE=2]*Bus 001 Device 002: ID 1b1c:1b0e Corsair Corsair K40A Gaming Keyboard*[/SIZE]
 [SIZE=2]*Bus 001 Device 003: ID 046d:c07e Logitech, Inc. G402 Gaming Mouse*[/SIZE]
 [SIZE=2]*Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/SIZE]
 
 
 But when I do lspci I get:
 
 
 [SIZE=2]*steve@PC:~/Downloads/rtl8812au-master$ lspci*[/SIZE]
 [SIZE=2]*00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex*[/SIZE]
 [SIZE=2]*00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU*[/SIZE]
 [SIZE=2]*00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge*[/SIZE]
 [SIZE=2]*00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge*[/SIZE]
 [SIZE=2]*00:03.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge*[/SIZE]
 [SIZE=2]*00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]*[/SIZE]
 [SIZE=2]*00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge*[/SIZE]
 [SIZE=2]*00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]*[/SIZE]
 [SIZE=2]*00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]*[/SIZE]
 [SIZE=2]*00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]*[/SIZE]
 [SIZE=2]*00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)*[/SIZE]
 [SIZE=2]*00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)*[/SIZE]
 [SIZE=2]*00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 0*[/SIZE]
 [SIZE=2]*00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 1*[/SIZE]
 [SIZE=2]*00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 2*[/SIZE]
 [SIZE=2]*00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 3*[/SIZE]
 [SIZE=2]*00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 4*[/SIZE]
 [SIZE=2]*00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 5*[/SIZE]
 [SIZE=2]*00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 6*[/SIZE]
 [SIZE=2]*00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 7*[/SIZE]
 [SIZE=2]*01:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43d0 (rev 01)*[/SIZE]
 [SIZE=2]*01:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller (rev 01)*[/SIZE]
 [SIZE=2]*01:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge (rev 01)*[/SIZE]
 [SIZE=2]*02:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)*[/SIZE]
 [SIZE=2]*02:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)*[/SIZE]
 [SIZE=2]*02:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)*[/SIZE]
 [SIZE=2]*02:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)*[/SIZE]
 [SIZE=2]*02:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)*[/SIZE]
 [SIZE=2]*02:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)*[/SIZE]
 [SIZE=2]*05:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)*[/SIZE]
 [SIZE=2]*08:00.0 USB controller: ASMedia Technology Inc. ASM1143 USB 3.1 Host Controller*[/SIZE]
 [SIZE=2]*09:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX 980 Ti] (rev a1)*[/SIZE]
 [SIZE=2]*09:00.1 Audio device: NVIDIA Corporation GM200 High Definition Audio (rev a1)*[/SIZE]
 [SIZE=2]*0a:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983*[/SIZE]
 [SIZE=2]*0b:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function*[/SIZE]
 [SIZE=2]*0c:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP*[/SIZE]
 [SIZE=2]*0c:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP*[/SIZE]
 [SIZE=2]*0c:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller*[/SIZE]
 [SIZE=2]*0c:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller*[/SIZE]
 [SIZE=2]*0d:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)*[/SIZE]
 [SIZE=2]*0e:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)*[/SIZE]
 
 
 From what I remember, I think I had to power the USB on or switch something on to get it to eventually work.
 
 
 So from not being able to install the wifi driver to not actually seeing it as an active device, what do I need to do?
 
 
 I have secure boot off too.

---

### Post by supercar55uk on 2022-06-21
Managed to fix it after a weeks work of searching the internet...

 [https://github.com/aircrack-ng/aircrack-ng](https://github.com/aircrack-ng/aircrack-ng)
 
 
 **[https://tutorialforlinux.com/2022/01/11/realtek-rtl8812au-driver-ubuntu-22-04-installation-step-by-step/2/](https://tutorialforlinux.com/2022/01/11/realtek-rtl8812au-driver-ubuntu-22-04-installation-step-by-step/2/)**
 
 
 Replace 8812au.ko with 88XXau.ko

---

### Post by coffeecat on 2022-06-21
*Thread moved to **Ubuntu/Debian Based**.*

---

