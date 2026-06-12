---
title: "wily werewolf overclock with wolfdale processor"
date: 2015-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2015-05-09
Having built a homemade 'Howler' air compressor out of spare parts and fitting it on top of a Wolfdale vPro Core 2 Duo I am getting preliminary speeds at 3.7GHz with very cool temps.

```

ventrical@ventrical-P5QL-PRO:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.39 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.23 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.07 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      4272 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +39.5°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +36.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +37.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +35.0°C  (high = +80.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +44.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-P5QL-PRO:~$ inxi -b
System:    Host: ventrical-P5QL-PRO Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.0 Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 3779 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (10.0% used)
Info:      Processes: 167 Uptime: 3 min Memory: 406.8/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ 

```

 Iv'e set a limit  for 60 degrees C and see where that takes me :) lol

Regards..

---

### Post by d-cosner on 2015-05-09
I would love to see a screen shot of that setup! I never thought of using a compressor but I bet one could be easily fashioned to work from a portable one that plugs into a car lighter. Might be kind of noisy though but you sure got me to thinking!

---

### Post by ventrical on 2015-05-09
Rolling up to near 4GHz and still cool.

```

ventrical@ventrical-P5QL-PRO:~$ inxi -b
System:    Host: ventrical-P5QL-PRO Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.0 Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 3959 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (10.0% used)
Info:      Processes: 178 Uptime: 0 min Memory: 259.4/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.38 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.23 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.07 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      4245 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +38.5°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +28.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +38.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +34.0°C  (high = +80.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +33.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)


```

```

ventrical@ventrical-P5QL-PRO:~$ systemd-analyze
Startup finished in 1.851s (kernel) + 13.570s (userspace) = 15.421s
ventrical@ventrical-P5QL-PRO:~$ 

```

---

### Post by ventrical on 2015-05-09
Howling @ 4.048GHz and cool.

```

ventrical@ventrical-P5QL-PRO:~$ inxi -b
System:    Host: ventrical-P5QL-PRO Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.0 Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 4048 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (10.0% used)
Info:      Processes: 172 Uptime: 0 min Memory: 255.7/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.41 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.23 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.07 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      4245 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +38.5°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +32.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +37.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +35.0°C  (high = +80.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +34.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)


```

not sure if my 800MHz ddr2 will be stable any higher... onward and upwards :)

Regards..

---

### Post by ventrical on 2015-05-09
> **d-cosner said:**
> I would love to see a screen shot of that setup! I never thought of using a compressor but I bet one could be easily fashioned to work from a portable one that plugs into a car lighter. Might be kind of noisy though but you sure got me to thinking!

Sorry .. it's not that kind of compressor. It is a high-speed 'fan' compressor. It blows air downwards and out against the heatsink. As the freq/voltage/heat increases so does the rpm of the fan. This one is off a server about circa 2005-07 or abouts.

Regards..

---

### Post by ventrical on 2015-05-09
4.048GHz is about is good as I am going to get. The issue is not temps .. it is now the memory brand.. will hopefully get some higher performance ddr2. until then ..

Regards..

---

### Post by ventrical on 2015-05-10
I upgraded an install from Precise to Trusty @ 4.005GHz which is processor intensive and the CPU temp did not go higher than 40C with one core only reaching 41C.

This was a successful  upgraded witht he exception that CAV would not bind to the new kernel (as I expected) Otherwise the overclock is exceptionally stable.

Regards..

---

