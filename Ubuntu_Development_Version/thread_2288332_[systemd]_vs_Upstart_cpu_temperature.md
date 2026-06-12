---
title: "[systemd] vs Upstart cpu temperature"
date: 2015-07-26
forum: Ubuntu Development Version
---

### Post by dgls on 2015-07-26
Hi all,
I notice an **increase** of CPU **temperature** up to 10°C strating Systemd instead Upstart.

Since Upotic, systemd behavior is the same about cpu heat. I tested in more laptops dual and quad core.
If there is a missing systemd service, why Upstart is cooler ?

Someone can confirm it ? How do I can fix ?
Thanks.

---

### Post by dino99 on 2015-07-26
hm, i've not seen such a difference on desktop nor laptop here (gnome-shell session)
but upstart is still available: install upstart-sysv to replace systemd-sysv, and you will get the upstart default booting choice (or simply select it into 'advanced' grub menu option

---

### Post by Rustan on 2015-07-26
maybe the problem is not systemd, as they say here [https://bugzilla.kernel.org/show_bug.cgi?id=90421](https://bugzilla.kernel.org/show_bug.cgi?id=90421)


intel_pstate is not working correctly, a Kernel 4.2RC1 seems bug fixed

---

### Post by QDR06VV9 on 2015-07-27
I have also noticed the hotter CPU Temps and also short Touch Mouse pad freezes on both Lenovo and Acer Lappy's.
Started noticing the Hotter Temps with kernel 4.0.6

> maybe the problem is not systemd, as they say here [https://bugzilla.kernel.org/show_bug.cgi?id=90421](https://bugzilla.kernel.org/show_bug.cgi?id=90421)


intel_pstate is not working correctly, a Kernel 4.2RC1 seems bug fixed
Going to test to see if any difference on 4.2RC1

---

### Post by dgls on 2015-07-27
I'm with kernel 4.1.2 and my temperature log is the following with both init systems for comparison:

```
--------------------------------------------------System Booted--------------------------------------------------

systemd

27/07/2015 - 08:40:28

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2665 MHz 2: 2665 MHz 3: 2665 MHz 4: 2665 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +44.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:       +47.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:       +47.0°C  (high = +105.0°C, crit = +105.0°C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  



systemd

27/07/2015 - 08:44:31

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2665 MHz 2: 2286 MHz 3: 1570 MHz 4: 1408 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +48.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +48.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:       +52.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:       +52.0°C  (high = +105.0°C, crit = +105.0°C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +48.0°C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  



systemd

27/07/2015 - 08:48:34

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2665 MHz 2: 2665 MHz 3: 1381 MHz 4: 1825 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +50.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +50.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:       +52.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:       +52.0°C  (high = +105.0°C, crit = +105.0°C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  



systemd

27/07/2015 - 08:52:37

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2148 MHz 2: 2023 MHz 3: 2665 MHz 4: 1408 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +52.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +52.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:       +55.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:       +55.0°C  (high = +105.0°C, crit = +105.0°C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  



systemd

27/07/2015 - 08:56:40

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2491 MHz 2: 2665 MHz 3: 1275 MHz 4: 1677 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +51.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:       +54.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:       +54.0°C  (high = +105.0°C, crit = +105.0°C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +51.0°C  



systemd

27/07/2015 - 09:00:43

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2572 MHz 2: 2665 MHz 3: 1991 MHz 4: 2647 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +50.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +52.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:       +53.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:       +53.0°C  (high = +105.0°C, crit = +105.0°C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +51.0°C  


--------------------------------------------------System Booted--------------------------------------------------

/sbin/upstart

27/07/2015 - 09:04:51

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2665 MHz 2: 2665 MHz 3: 2434 MHz 4: 2522 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0 C  (crit = +105.0 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0 C  (high = +105.0 C, crit = +105.0 C)
Core 1:       +51.0 C  (high = +105.0 C, crit = +105.0 C)
Core 2:       +54.0 C  (high = +105.0 C, crit = +105.0 C)
Core 3:       +54.0 C  (high = +105.0 C, crit = +105.0 C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +51.0 C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +51.0 C  



/sbin/upstart

27/07/2015 - 09:08:52

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 706 MHz 2: 1097 MHz 3: 628 MHz 4: 1474 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +46.0 C  (crit = +105.0 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +45.0 C  (high = +105.0 C, crit = +105.0 C)
Core 1:       +45.0 C  (high = +105.0 C, crit = +105.0 C)
Core 2:       +47.0 C  (high = +105.0 C, crit = +105.0 C)
Core 3:       +48.0 C  (high = +105.0 C, crit = +105.0 C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +45.0 C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +46.0 C  



/sbin/upstart

27/07/2015 - 09:12:54

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 825 MHz 2: 1069 MHz 3: 1873 MHz 4: 1445 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  (crit = +105.0 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0 C  (high = +105.0 C, crit = +105.0 C)
Core 1:       +44.0 C  (high = +105.0 C, crit = +105.0 C)
Core 2:       +47.0 C  (high = +105.0 C, crit = +105.0 C)
Core 3:       +47.0 C  (high = +105.0 C, crit = +105.0 C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +45.0 C  



/sbin/upstart

27/07/2015 - 09:16:56

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 759 MHz 2: 961 MHz 3: 1407 MHz 4: 1672 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  (crit = +105.0 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0 C  (high = +105.0 C, crit = +105.0 C)
Core 1:       +43.0 C  (high = +105.0 C, crit = +105.0 C)
Core 2:       +46.0 C  (high = +105.0 C, crit = +105.0 C)
Core 3:       +46.0 C  (high = +105.0 C, crit = +105.0 C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +43.0 C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  



/sbin/upstart

27/07/2015 - 09:20:57

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 2493 MHz 2: 2117 MHz 3: 1672 MHz 4: 2496 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  (crit = +105.0 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0 C  (high = +105.0 C, crit = +105.0 C)
Core 1:       +43.0 C  (high = +105.0 C, crit = +105.0 C)
Core 2:       +46.0 C  (high = +105.0 C, crit = +105.0 C)
Core 3:       +46.0 C  (high = +105.0 C, crit = +105.0 C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +43.0 C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  



/sbin/upstart

27/07/2015 - 09:22:58

CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17305
           clock speeds: min/max: 499/2665 MHz 1: 1531 MHz 2: 1192 MHz 3: 1450 MHz 4: 2184 MHz

acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  (crit = +105.0 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0 C  (high = +105.0 C, crit = +105.0 C)
Core 1:       +43.0 C  (high = +105.0 C, crit = +105.0 C)
Core 2:       +45.0 C  (high = +105.0 C, crit = +105.0 C)
Core 3:       +45.0 C  (high = +105.0 C, crit = +105.0 C)

soc_dts0-virtual-0
Adapter: Virtual device
temp1:        +43.0 C  

soc_dts1-virtual-0
Adapter: Virtual device
temp1:        +44.0 C  


```

I don't think is a kernel issue... Upstart can handle heat better than Systemd with the same services.
Is not possible work this way... an increase of **10 degrees** is not healtly.

---

### Post by QDR06VV9 on 2015-07-27
I am thinking it could be a combo of both systemd and kernel
```
inxi -Fxz
System:    Host: me-Aspire-5750 Kernel: 4.2.0-040200rc4-lowlatency x86_64 (64 bit gcc: 4.8.4)
           Desktop: N/A Distro: Ubuntu 15.10 wily
Machine:   System: Acer product: Aspire 5750 v: V1.14
           Mobo: Acer model: JE50_HR Bios: Acer v: V1.14 date: 09/07/2011
CPU:       Dual core Intel Core i3-2330M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8780
           clock speeds: max: 2200 MHz 1: 892 MHz 2: 801 MHz 3: 810 MHz
           4: 839 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.0hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 10.5.9 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: ALSA v: k4.2.0-040200rc4-lowlatency
Network:   Card-1: Broadcom NetLink BCM57785 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi bus-ID: 03:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 160.0GB (10.3% used)
           ID-1: /dev/sda model: Hitachi_HTS54161 size: 160.0GB
Partition: ID-1: / size: 143G used: 12G (9%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.14GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 51.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 191 Uptime: 3 min Memory: 337.9/3805.4MB
           Init: systemd runlevel: 5 Gcc sys: 4.9.3
           Client: Shell (bash 4.3.301) inxi: 2.2.16 

```

Touch pad seems a little smother although only been running this kernel for a few minutes now
**but a cooler temp is noticed on the cpu.**
But that may be just my specs
Regards
This after
Just installed upstart & reboot to upstart, and have not noticed any temp difference yet?
```
 apt-cache policy upstart
upstart:
  Installed: 1.13.2-0ubuntu14
  Candidate: 1.13.2-0ubuntu14
  Version table:
 *** 1.13.2-0ubuntu14 0
        500 http://archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Linuxisfast on 2015-10-15
My experience is with Arch and Ubuntu 14.04.3 LTS. Both running on Intel Haswell 4790, in Ubuntu the machine runs smoother and same version Google Chrome browser runs better but in case of Arch with latest Kernel 4.1 and systemd, the CPU temps spike 10c higher with same tasks that are on Ubuntu. I am glad someone noticed this but also there has been a discussion about how Arch kernel is tuned at 300MHz compared to Ubuntu Kernel at 1000MHz for clock.

---

### Post by Doug S on 2015-10-15
> **Linuxisfast said:**
> ... but also there has been a discussion about how Arch kernel is tuned at 300MHz compared to Ubuntu Kernel at 1000MHz for clock.Yes, some of that discussion turned out to be incorrect. However, while the issues are there anyhow, there does seem to be some interesting increased manifestations due to the 300 Hertz verses the 1000Hz low latency or the standard 250Hz Ubuntu kernels.

Increased CPU temperature investigations that I have been involved with have mostly been after a resume from suspend and usually related to CPU's not going into high numbered C states after the resume, resulting in much more power consumption. A secondary effect has been the CPU frequencies do not drop down to the lowest levels anymore, but typically, and depending on the processor, this only explains about a 1/2 watt increase in overall processor power consumption.
  
I would recommend sufferers to use turbostat to obtain information as to C states and temperatures. Example:```
doug@s15:~/temp$ [COLOR="#FF0000"]sudo ./turbostat -d sleep 10[/COLOR]
turbostat version 4.7 17-June, 2015 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(6): APERF, DTS, PTM, EPB
RAPL: 690 sec. Joule Counter Range, at 95 Watts
cpu0: MSR_NHM_PLATFORM_INFO: 0x100070012200
16 * 100 = 1600 MHz max efficiency frequency
34 * 100 = 3400 MHz base frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu0: MSR_TURBO_RATIO_LIMIT: 0x23242526
35 * 100 = 3500 MHz max turbo 4 active cores
36 * 100 = 3600 MHz max turbo 3 active cores
37 * 100 = 3700 MHz max turbo 2 active cores
38 * 100 = 3800 MHz max turbo 1 active cores
cpu0: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e008403 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=3: pc6r)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x01e002f8 (95 W TDP, RAPL 60 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)
cpu0: PKG Limit #1: ENabled (255.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: ENabled (255.000000 Watts, 0.000977* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00621200 (98 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88430000 (31 C)
cpu0: MSR_IA32_THERM_STATUS: 0x88450000 (29 C +/- 1)
cpu1: MSR_IA32_THERM_STATUS: 0x88430000 (31 C +/- 1)
cpu2: MSR_IA32_THERM_STATUS: 0x88440000 (30 C +/- 1)
cpu3: MSR_IA32_THERM_STATUS: 0x88430000 (31 C +/- 1)
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 PkgWatt CorWatt GFXWatt
       -       -       0    0.03    [COLOR="#FF0000"]1616[/COLOR]    3411       0    1.00    0.02   98.95    0.00      [COLOR="#FF0000"]24[/COLOR]      [COLOR="#FF0000"]25[/COLOR]    1.95    0.04   [COLOR="#FF0000"]94.08[/COLOR]    [COLOR="#FF0000"]3.97[/COLOR]    [COLOR="#FF0000"]0.36    0.23[/COLOR]
       0       0       1    0.06    1612    3411       0    3.74    0.06   96.14    0.00      24      25    1.95    0.04   94.08    3.97    0.36    0.23
       0       4       0    0.02    1611    3411       0    3.77
       1       1       0    0.02    1608    3411       0    0.06    0.00   99.92    0.00      24
       1       5       0    0.02    1643    3411       0    0.06
       2       2       0    0.02    1613    3411       0    0.05    0.00   99.93    0.00      24
       2       6       0    0.02    1624    3411       0    0.05
       3       3       1    0.06    1615    3411       0    0.10    0.03   99.82    0.00      24
       3       7       0    0.01    1611    3411       0    0.14
10.001397 sec
doug@s15:~/temp$ [COLOR="#FF0000"]sudo pm-suspend[/COLOR]
doug@s15:~/temp$ [COLOR="#FF0000"]sudo ./turbostat -d sleep 10[/COLOR]
turbostat version 4.7 17-June, 2015 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(6): APERF, DTS, PTM, EPB
RAPL: 690 sec. Joule Counter Range, at 95 Watts
cpu6: MSR_NHM_PLATFORM_INFO: 0x100070012200
16 * 100 = 1600 MHz max efficiency frequency
34 * 100 = 3400 MHz base frequency
cpu6: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu6: MSR_TURBO_RATIO_LIMIT: 0x23242526
35 * 100 = 3500 MHz max turbo 4 active cores
36 * 100 = 3600 MHz max turbo 3 active cores
37 * 100 = 3700 MHz max turbo 2 active cores
38 * 100 = 3800 MHz max turbo 1 active cores
cpu6: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e008403 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=3: pc6r)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x01e002f8 (95 W TDP, RAPL 60 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)
cpu0: PKG Limit #1: ENabled (255.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: ENabled (255.000000 Watts, 0.000977* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00621200 (98 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x883a0000 (40 C)
cpu0: MSR_IA32_THERM_STATUS: 0x88400000 (34 C +/- 1)
cpu1: MSR_IA32_THERM_STATUS: 0x88410000 (33 C +/- 1)
cpu2: MSR_IA32_THERM_STATUS: 0x88400000 (34 C +/- 1)
cpu3: MSR_IA32_THERM_STATUS: 0x88400000 (34 C +/- 1)
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 PkgWatt CorWatt GFXWatt
       -       -       0    0.01    [COLOR="#FF0000"]2426[/COLOR]    3411       0    0.06    0.00   99.93    0.00      [COLOR="#FF0000"]35      38  [/COLOR]  0.00    0.00    [COLOR="#FF0000"]0.00   10.04    3.03    3.49[/COLOR]
       0       0       1    0.05    2421    3411       0    0.09    0.01   99.84    0.00      33      38    0.00    0.00    0.00   10.04    3.03    3.49
       0       4       0    0.01    2415    3411       0    0.14
       1       1       0    0.02    2467    3411       0    0.04    0.00   99.95    0.00      33
       1       5       0    0.01    2419    3411       0    0.04
       2       2       0    0.01    2423    3411       0    0.04    0.00   99.95    0.00      34
       2       6       0    0.01    2416    3411       0    0.04
       3       3       0    0.01    2418    3411       0    0.03    0.00   99.97    0.00      35
       3       7       0    0.01    2418    3411       0    0.02
10.001024 sec
```Note: My example is based on a different issue, and is just to demonstrate what to look for.

---

