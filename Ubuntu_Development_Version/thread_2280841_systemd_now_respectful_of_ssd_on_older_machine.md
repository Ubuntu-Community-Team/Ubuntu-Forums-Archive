---
title: "systemd now respectful of ssd on older machine"
date: 2015-06-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-06-02
Major load of updates and after reboot got this:

```

ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 1.829s (kernel) + 7.558s (userspace) = 9.388s
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.38 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.22 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.07 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      4245 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +38.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +34.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +37.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +33.0°C  (high = +80.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +34.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-20-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 4004 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (6.6% used)
Info:      Processes: 175 Uptime: 1 min Memory: 421.7/2000.3MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-System-Product-Name:~$ 

```

...so systemd is gathering some lightning and thunder it appears. :)

Regards..

---

### Post by P-I H on 2015-06-03
My system boots a little faster too.
The kernel time is about the same, but user space takes about 3 sec less.
```
p-i@pi-GA-MA770-UD3-SSD:~$ systemd-analyze
Startup finished in 4.618s (kernel) + 4.642s (userspace) = 9.261s
p-i@pi-GA-MA770-UD3-SSD:~$ sensors
it8720-isa-0228
Adapter: ISA adapter
in0:          +1.39 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.36 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +3.06 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.06 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.65 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.26 V  
fan1:         965 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan5:        1430 RPM  (min =    0 RPM)
temp1:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +38.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
temp3:        +82.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
intrusion0:  ALARM


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +24.9°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)


radeon-pci-0100
Adapter: PCI adapter
temp1:        +40.0°C  (crit = +120.0°C, hyst = +90.0°C)


p-i@pi-GA-MA770-UD3-SSD:~$ inxi -b
System:    Host: pi-GA-MA770-UD3-SSD Kernel: 3.19.0-20-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: Gigabyte model: GA-MA770-UD3 v: x.x
           Bios: Award v: FKb date: 07/08/2010
CPU:       Quad core AMD Athlon II X4 620 (-MCP-) speed: 2999 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Turks XT [Radeon HD 6670/7670]
           Display Server: X.Org 1.17.1 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1680x1050@60.0hz
           GLX Renderer: Gallium 0.4 on AMD TURKS GLX Version: 3.0 Mesa 10.5.2
Network:   Card-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
           driver: ath9k
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 760.2GB (4.3% used)
Info:      Processes: 209 Uptime: 6 min Memory: 1020.9/3948.7MB
           Client: Shell (bash) inxi: 2.2.16 
p-i@pi-GA-MA770-UD3-SSD:~$
```

---

