---
title: "Virtualbox Windows 10 Guests Crashing Repeatedly"
date: 2021-06-03
forum: Virtualisation
---

### Post by mootpoint on 2021-06-03
I have Windows 10 guests crashing repeatedly in Virtualbox. They will stay up and running for anywhere from 15 minutes to an hour, then crash and reload. A few Windows error messages (on the rare occasion there is one) include KMODE_EXCEPTION_NOT_HANDLED, INTERRUPT_EXCEPTION_NOT_HANDLED, DRIVER_OVERRAN_STACK_BUFFER, and IRQL_NOT_LESS_OR_EQUAL. A look at the VBox log files shows little of interest to my uninformed eye; they report that the guest has reported the error and become unresponsive. I have both VBox log files and a couple of Windows 10 memory dump files available. I have tried the following all with no change in results:

1) I have uninstalled and reinstalled Virtualbox.
2) I tried to install the virtualbox .deb files from Oracle, but ran into dependency issues and stopped. 
3) I have created a new guest from scratch using Microsoft's .img file. It behaves the same way the older one does.
4) I have converted the .vdi to a qcow2. The resulting image is stable when run under KVM. 
5) The guests have the Guest Additions installed and are the same version as Virtualbox. 
6) There's no pattern to the crashes I can discern. Almost all happen when the vm is just sitting there. 
7) I created a Linux guest VM, which has been sitting here for an hour with no issues at least so far. 

The hardware is a new Dell Inspiron laptop. I installed Linux Mint on it. The installation process automagically loaded kernel 5.8.0-53 to handle the hardware. Everything else is working fine. I'm more than happy to upload log files and memory dump files if someone tells me where/how to do so. 

Would surely appreciate some help on this. Thanks in advance!

mootpoint

```
System:    Host: lapdog Kernel: 5.8.0-53-generic x86_64 bits: 64 compiler: N/A Desktop: Cinnamon 4.8.6 
           Distro: Linux Mint 20.1 Ulyssa base: Ubuntu 20.04 focal 
Machine:   Type: Laptop System: Dell product: Inspiron 5502 v: N/A serial: <superuser/root required> 
           Mobo: Dell model: 0WNVYK v: A00 serial: <superuser/root required> UEFI: Dell v: 1.4.1 date: 03/30/2021 
Battery:   ID-1: BAT0 charge: 47.3 Wh condition: 53.0/53.0 Wh (100%) model: SMP DELL 9077G11 status: Unknown 
           Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M315/M235 charge: 55% (should be ignored) 
           status: Discharging 
Memory:    RAM: total: 23.22 GiB used: 14.51 GiB (62.5%) 
           RAM Report: permissions: Unable to run dmidecode. Root privileges required. 
CPU:       Topology: Quad Core model: 11th Gen Intel Core i5-1135G7 bits: 64 type: MT MCP arch: Tiger Lake rev: 1 
           L2 cache: 8192 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 22118 
           Speed: 2233 MHz min/max: 400/4200 MHz Core speeds (MHz): 1: 2273 2: 3100 3: 699 4: 1092 5: 2238 6: 3099 7: 2581 
           8: 1177 
Graphics:  Device-1: Intel vendor: Dell driver: i915 v: kernel bus ID: 0000:00:02.0 
           Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz, 1920x1080~60Hz, 2560x1440~60Hz, 2560x1440~60Hz 
           OpenGL: renderer: Mesa Intel Xe Graphics (TGL GT2) v: 4.6 Mesa 20.2.6 direct render: Yes 
Network:   Device-1: Intel driver: iwlwifi v: kernel port: 3000 bus ID: 0000:00:14.3 
           IF: wlp0s20f3 state: up mac: 28:d0:ea:ed:c3:58 
           IF-ID-1: virbr0 state: down mac: 52:54:00:a6:3c:15 
           IF-ID-2: virbr0-nic state: down mac: 52:54:00:a6:3c:15 
Drives:    Local Storage: total: 591.55 GiB used: 312.09 GiB (52.8%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: PM991a NVMe 256GB size: 238.47 GiB 
           ID-2: /dev/nvme1n1 model: PC SN720 NVMe WDC 512GB size: 476.94 GiB 
           ID-3: /dev/sda type: USB vendor: SanDisk model: USB 3.2Gen1 size: 114.61 GiB 
Partition: ID-1: / size: 31.83 GiB used: 12.85 GiB (40.4%) fs: ext4 dev: /dev/nvme0n1p3 
           ID-2: /home size: 183.82 GiB used: 110.43 GiB (60.1%) fs: ext4 dev: /dev/nvme0n1p7 
Sensors:   System Temperatures: cpu: 44.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 3701 
Info:      Processes: 404 Uptime: 1d 6h 53m Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
```

---

