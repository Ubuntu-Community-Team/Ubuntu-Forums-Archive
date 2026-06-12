---
title: "kernel 4.18.0.10-11 early crashing"
date: 2018-10-13
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-10-13
That kernel is unusable on a skylake mobo+i5 cpu

it early crash at grub level, saying: please append a correct root= path
but it has exactly the same root='hd2,msdos1' path as the previous kernel 4.18.0.9
everything seems correct: blkid & fstab are matching.

I have purged then reinstalled it, but to no avail.
It crash too early to get something logged.
Sadly that version has now been pushed to 'main'.;)

---

### Post by P-I H on 2018-10-13
The 4.18.0-10 kernel is working on my system. However power draw from the wall outlet is about 50 watts higher compared to the 4.18.0-08 kernel. It's the same with the 4.18.0-09 ```
kernel.p-i@pi-MS-7A34:~$ inxi -FSystem:    Host: pi-MS-7A34 Kernel: 4.18.0-8-generic x86_64 bits: 64 Desktop: Gnome 3.30.1 
           Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <root required> 
           UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1375 MHz min/max: 1550/3000 MHz Core speeds (MHz): 1: 1377 2: 1376 3: 1377 4: 1372 5: 1380 
           6: 1451 7: 1376 8: 1376 9: 1377 10: 1374 11: 1378 12: 1374 13: 1377 14: 1374 15: 1382 16: 1380 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X] 
           driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.1 driver: amdgpu tty: N/A 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.26.0 4.18.0-8-generic LLVM 7.0.0) 
           v: 4.5 Mesa 18.2.2 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580] driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k4.18.0-8-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: 4c:cc:6a:f4:2d:5e 
Drives:    Local Storage: total: 689.34 GiB used: 125.70 GiB (18.2%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition: ID-1: / size: 227.74 GiB used: 125.69 GiB (55.2%) fs: ext4 dev: /dev/nvme0n1p2 
Sensors:   System Temperatures: cpu: 37.0 C mobo: 38.0 C gpu: amdgpu temp: 35 C 
           Fan Speeds (RPM): fan-1: 507 fan-2: 571 fan-3: 976 fan-4: 0 fan-5: 751 fan-6: 0 gpu: amdgpu 
           fan: 1150 
Info:      Processes: 349 Uptime: 7m Memory: 15.68 GiB used: 1.79 GiB (11.4%) Shell: bash inxi: 3.0.24 
p-i@pi-MS-7A34:~$ 
```
Sensors on the 4.18.0-10 kernel
```
p-i@pi-MS-7A34:~$ sensors
nct6795-isa-0a20
Adapter: ISA adapter
in0:                    +0.85 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +0.15 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.69 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in11:                   +1.05 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +0.92 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +0.68 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +1.54 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   510 RPM  (min =    0 RPM)
fan2:                   575 RPM  (min =    0 RPM)
fan3:                   984 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   785 RPM  (min =    0 RPM)
fan6:                     0 RPM  (min =    0 RPM)
SYSTIN:                 +39.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                 +38.0°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                +43.5°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:               -128.0°C    sensor = thermistor
AUXTIN2:                +23.0°C    sensor = thermistor
AUXTIN3:                 -3.0°C    sensor = thermistor
SMBUSMASTER 0:          +35.0°C  
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled


k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +35.2°C  (high = +70.0°C)
Tctl:         +35.2°C  


amdgpu-pci-2300
Adapter: PCI adapter
vddgfx:       +1.17 V  
fan1:        1160 RPM
temp1:        +43.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       53.19 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$
```
Sensors on the 4.18.0-08 kernel
```
p-i@pi-MS-7A34:~$ sensors
nct6795-isa-0a20
Adapter: ISA adapter
in0:                    +0.85 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +0.15 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.66 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in11:                   +1.05 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +0.92 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +0.68 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +1.54 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   515 RPM  (min =    0 RPM)
fan2:                   585 RPM  (min =    0 RPM)
fan3:                   996 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   776 RPM  (min =    0 RPM)
fan6:                     0 RPM  (min =    0 RPM)
SYSTIN:                 +39.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                 +39.0°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                +45.5°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:               -128.0°C    sensor = thermistor
AUXTIN2:                +23.0°C    sensor = thermistor
AUXTIN3:                 -3.0°C    sensor = thermistor
SMBUSMASTER 0:          +36.0°C  
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled


k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +35.8°C  (high = +70.0°C)
Tctl:         +35.8°C  


amdgpu-pci-2300
Adapter: PCI adapter
vddgfx:       +0.72 V  
fan1:        1228 RPM
temp1:        +36.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       30.13 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$

```
The increase is mostly from the Radeon RX580 gpu as shown in this article by Phoronix.
[https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-4.18-Power-Draw](https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-4.18-Power-Draw)

---

### Post by PaulW2U on 2018-10-13
> **dino99 said:**
> Sadly that version has now been pushed to 'main'.;)
Interesting. After a very recent update I have the following installed:
```
paul@N1643~> v /boot
total 159504
drwxr-xr-x  3 root root     4096 Oct 13 12:15 ./
drwxr-xr-x 25 root root     4096 Oct 13 11:18 ../
drwxr-xr-x  5 root root     4096 Oct 13 12:27 grub/
-rw-r--r--  1 root root  1504494 Oct 11 14:24 abi-4.18.0-10-generic
-rw-r--r--  1 root root  1479894 Sep 10 13:08 abi-4.18.0-8-generic
-rw-r--r--  1 root root  1479938 Oct  5 17:13 abi-4.18.0-9-generic
-rw-r--r--  1 root root   217050 Oct 11 14:24 config-4.18.0-10-generic
-rw-r--r--  1 root root   217064 Sep 10 13:08 config-4.18.0-8-generic
-rw-r--r--  1 root root   217037 Oct  5 17:13 config-4.18.0-9-generic
-rw-r--r--  1 root root 39641321 Oct 13 12:15 initrd.img-4.18.0-10-generic
-rw-r--r--  1 root root 39633554 Oct 11 19:19 initrd.img-4.18.0-8-generic
-rw-r--r--  1 root root 39640203 Oct 12 15:37 initrd.img-4.18.0-9-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root       17 Oct 11 14:24 retpoline-4.18.0-10-generic
-rw-r--r--  1 root root       17 Sep 10 13:08 retpoline-4.18.0-8-generic
-rw-r--r--  1 root root       17 Oct  5 17:13 retpoline-4.18.0-9-generic
-rw-------  1 root root  4355913 Oct 11 14:24 System.map-4.18.0-10-generic
-rw-------  1 root root  4354064 Sep 10 13:08 System.map-4.18.0-8-generic
-rw-------  1 root root  4355913 Oct  5 17:13 System.map-4.18.0-9-generic
-rw-------  1 root root  8544088 Oct 11 14:28 vmlinuz-4.18.0-10-generic
-rw-r--r--  1 root root  8535896 Oct  2 10:12 vmlinuz-4.18.0-8-generic
-rw-------  1 root root  8544088 Oct  5 17:14 vmlinuz-4.18.0-9-generic

```
but I can only boot to:
```
paul@N1643~> uname -a
Linux N1643 4.18.0-8-generic #9-Ubuntu SMP Mon Sep 10 16:12:10 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by dino99 on 2018-10-13
Due to your comments, i have made some more tweaks via synaptic:
- purged all '10' kernel packages
- purged linux-generic and the left over packages: thermald & amd-decode

Then via synaptic trying to install linux-generic, it list all the packages as expected, but fails to install on linux-generic (broken deps).
But the same install goes well via the terminal  !!!!

Going to try booting on it now :P

Result: still fails.
Going to suspect some grub conflicts : that desktop has 4 ubuntu installations on 3 devices, with a grub on each, but the 'main' grub' listing the others is on a Bionic one.
Purging then reinstalling the 'master' grub finally solved that problem  :p

So no problem with that kernel, but a grub conflict somewhere. (i am now logged on '10' kernel)

---

### Post by PaulW2U on 2018-10-13
> **dino99 said:**
> So no problem with that kernel, but a grub conflict somewhere. (i am now logged on '10' kernel)
Definitely a grub problem here too as I couldn't select either -9 or -10 even after reinstalling grub. -8 was my only option.

As I'm dual booting I booted into Bionic and reinstalled grub there. When rebooting I found all Cosmic kernels were available so I'm also now using -10.

---

### Post by P-I H on 2018-10-13
Didn't want to wait on a kernel update.
Installed kernel 4.18.0-14 and now the power draw is as expected 64W-65W.
```
p-i@pi-MS-7A34:~$ sensors
nct6795-isa-0a20
Adapter: ISA adapter
in0:                    +0.85 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +0.15 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.70 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in11:                   +1.06 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +0.92 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +0.68 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +1.54 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   510 RPM  (min =    0 RPM)
fan2:                   573 RPM  (min =    0 RPM)
fan3:                   981 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   770 RPM  (min =    0 RPM)
fan6:                     0 RPM  (min =    0 RPM)
SYSTIN:                 +37.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                 +35.0°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                +43.5°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:               -128.0°C    sensor = thermistor
AUXTIN2:                +23.0°C    sensor = thermistor
AUXTIN3:                 -3.0°C    sensor = thermistor
SMBUSMASTER 0:          +32.0°C  
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled


k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +32.0°C  (high = +70.0°C)
Tctl:         +32.0°C  


amdgpu-pci-2300
Adapter: PCI adapter
vddgfx:       +0.72 V  
fan1:        1162 RPM
temp1:        +31.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       30.21 W  (cap = 165.00 W)


p-i@pi-MS-7A34:~$ 

```

---

