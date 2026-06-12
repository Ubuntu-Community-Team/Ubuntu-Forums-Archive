---
title: "Lenovo G70 screen flicker"
date: 2016-11-08
forum: Ubuntu Development Version
---

### Post by jerrynewt on 2016-11-08
Intel® Core™ i7-5500U CPU @ 2.40GHz × 4, Intel® HD Graphics 5500 (Broadwell GT2). After upgrade to Zesty the screen if flickering and mouse function is sporadic. Checking for additional drivers I see message saying  1 proprietary driver in use (shown as unknown) "using Processor microcode firmware for Intel CPU's from intel-microcode (proprietary)". Any ideas on a workaround??

---

### Post by jerrynewt on 2016-11-09
Anyone have any ideas??

---

### Post by VinDSL on 2016-11-11
This will probably be of no help to you, but I wanted to confirm that I have the same flickering problem with my nVidia chipset.

Actually, it was beyond flickering, when I first rebased to 17.04.  It was actually flashing like a neon sign.

The fix for the flashing was to blacklist Nouveau and install nVidia drivers.  Now, I just have flickering, especially in CLI.

We'll get there.  It's still early in the cycle ...  ;)

---

### Post by ventrical on 2016-11-11
I get this:
```

update-initramfs: Generating /boot/initrd.img-4.8.0-27-generic
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915

```

on most of my intel graphics installs but I don't get the flickerty

I had the flickerty once but then:
```

sudo apt-get install nouveau-firmware

```

and it solved but the error still comes up in terminal.

Look at the driver it is using..

```
ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.8.0-26-generic x86_64 (64 bit gcc: 6.2.0)
           Desktop: Unity 7.5.0 (Gtk 3.22.2-0ubuntu1)
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: desktop Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           UEFI: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12400
           clock speeds: max: 3100 MHz 1: 1315 MHz 2: 1264 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 12.0.3 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.8.0-26-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 128.0GB (20.9% used)
           ID-1: /dev/sda model: SAMSUNG_MZ7PA128 size: 128.0GB
Partition: ID-1: / size: 113G used: 22G (20%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 4.15GB used: 0.06GB (2%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 236 Uptime: 4 days Memory: 1821.8/3813.7MB
           Init: systemd runlevel: 5 Gcc sys: 6.2.0
           Client: Shell (bash 4.3.461) inxi: 2.3.4 
ventrical@ventrical-MS-7850:~$ 

```

---

