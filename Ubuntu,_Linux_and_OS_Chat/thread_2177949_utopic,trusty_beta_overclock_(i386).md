---
title: "utopic,trusty beta overclock (i386)"
date: 2013-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2013-10-01
Just thought I would start a new topic rather than to drop off-topic overclock subject matter on other threads.

I was reading a thread started by kansasnoob about Gnome-flashback ..etc.. and so I installed it in a certain way that I do using fvwm-crystal. I am currently running gnome-session-flashback at an overclock speed on a Pentium 4 3.20GHz @ 4.297GHz on stock cooling. This is a hyperthreading processor and I am using ccsm ring-swtcher feature with no unstability apparent.  I am going to set a goal for 4.8 GHz on stock cooling running gnome-flashback. Anyone else overclocking saucy beta is welcome to jump in.

regards..


  ```


ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +30.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4297 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4330 GHz by steps of 2

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4090 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4330 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4343

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4141 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudodmidecode -t processor | grep "Speed"
sudodmidecode: command not found
ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4343 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
Ok... ran into a wall. Adjusted PCIe freq from 100 to 102MHz. No lock ups at 4.375 GHz

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +22.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4375 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

cpu freq 273
Dram freq 409
PM Turbo
PCIe 102
PCI clk sync 33.33
Mem V 1.95
Vcore 1.5375

---

### Post by ventrical on 2013-10-01
4.407

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +30.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +22.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmideocde -t processor | grep "Speed"
[sudo] password for ventrical: 
sudo: dmideocde: command not found
ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 4407 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.439

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4439 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.471

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +22.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4471 MHz

```

---

### Post by ventrical on 2013-10-01
4.503 GHz

Time for a break ! :) ... and hopefully not breakage ! :) lol

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +37.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4503 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.534

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +33.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +24.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +31.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4534 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.567

```

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4567 MHz
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +35.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +20.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +35.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.599GHz

It should start to get unstable now and I will need to pump the Vcore, mem volts and PCIe freq.

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +30.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4599 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.631GHz

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +37.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +30.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4631 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
Look how low the threads are running.

---

### Post by ventrical on 2013-10-01
4.663GHz

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +28.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +35.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4663 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.726 GHz

```

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4726 MHz
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4141 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +34.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
4.805GHz

```

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4805 MHz
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +38.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +33.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400

```

Ok... I am going to work with it here for a while :)   whew !

---

### Post by pqwoerituytrueiwoq on 2013-10-01
how many hours of prime have you ran? i really doubt you can get clock speeds like that on stock cooling and be stable
prime95 has a linux version, mprime
the only cpu i have overclocked is my phenom II 965
highest i got to was 4.2GHz and that is not stock cooling (CM Hyper 212 evo)
if it is not stable it does not count IMO

---

### Post by ventrical on 2013-10-01
Currently at 53C

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.53 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.65 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.04 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +54.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +33.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +28.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +38.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

```

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4805 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2013-10-01
> **pqwoerituytrueiwoq said:**
> how many hours of prime have you ran? i really doubt you can get clock speeds like that on stock cooling and be stable
prime95 has a linux version, mprime
the only cpu i have overclocked is my phenom II 965
highest i got to was 4.2GHz and that is not stock cooling (CM Hyper 212 evo)
if it is not stable it does not count IMO


 I got ccsm cube+rotate etc... working like a charm. Hasn't even blinked. I should try the seti@home and see whats up.

 I have an another ASUS tower with AMD64 Athlon 5000+ 2X Dual Core and it is really touchy when trying to overclock. It gets hot really fast.. but I'm working on it. I build my own experimental heat syncs and I am going to get to that later.

---

### Post by QDR06VV9 on 2013-10-01
> **ventrical said:**
> I got ccsm cube+rotate etc... working like a charm. Hasn't even blinked. I should try the seti@home and see whats up.

 I have an another ASUS tower with AMD64 Athlon 5000+ 2X Dual Core and it is really touchy when trying to overclock. It gets hot really fast.. but I'm working on it. I build my own experimental heat syncs and I am going to get to that later.

I ran that same chip @ 2.95 for about 2 years with thermake cooler before it split..
Overclocked always on!

---

### Post by ventrical on 2013-10-01
Ok.. I did a litle over 2 hours with an average of 53C CPU temp. I'll get back later and add some more assignments to worktodo.txt when i got some idle time.

btw .. Thanks for your interest. :)

---

### Post by ventrical on 2013-10-01
> **runrickus said:**
> I ran that same chip @ 2.95 for about 2 years with thermake cooler before it split..
Overclocked always on!

 Thats a good overclock for that long.  I had it at 3.4 but it got too hot .. so I have to finester some things around with that. it runs just fine @ 2.77GHz .. :) lol but I hear it can run stable at high speeds. I may be getting a AMD642X6000+ to play around with and AM3 board... but I have to work with what I got for now.

  I guess my main point is , is that saucy beta (gnome-flashback) is running really stable at these high speeds.

 I have a surplus of intel 3.45GHs , 3.20GHz and some Celeron 3.20GHz (Cedar Mill) which is what I want for over 5 GHz.. so I am not worried about popping processors. I am going to try and delid a few of the 3.45 Pentiums and re-paste them and see if I can get them cooler.

Regards..

---

### Post by ventrical on 2013-10-02
5.030GHz

```

Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.57 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.04 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4041 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +41.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +15.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5030 MHz

```

---

### Post by ventrical on 2013-10-02
Still running cool.. :)

---

### Post by ventrical on 2013-10-02
mprime status

```

     4.  Test/Continue
     5.  Test/Exit
     6.  Advanced/Test
     7.  Advanced/Time
     8.  Advanced/P-1
     9.  Advanced/ECM
    10.  Advanced/Manual Communication
    11.  Advanced/Unreserve Exponent
    12.  Advanced/Quit Gimps
    13.  Options/CPU
    14.  Options/Preferences
    15.  Options/Torture Test
    16.  Options/Benchmark
    17.  Help/About
    18.  Help/About PrimeNet Server
Your choice: 3

Below is a report on the work you have queued and any expected completion 
dates.
M62406301, Lucas-Lehmer test, Sun Dec 15 21:04 2013
The chance that the exponent you are testing will yield a Mersenne prime 
is about 1 in 474143. 

Hit enter to continue: 

```

The web server even validated my CPU speed.

```

Please see the readme.txt file for important
information on the P-1/ECM stage 2 memory settings.

Daytime P-1/ECM stage 2 memory in MB (8): 
Nighttime P-1/ECM stage 2 memory in MB (8): 

CPU Information:
Intel(R) Pentium(R) 4 CPU 3.20GHz
CPU speed: 5027.02 MHz, with hyperthreading
CPU features: Prefetch, SSE, SSE2
L1 cache size: 16 KB
L2 cache size: 2 MB


```

---

### Post by ventrical on 2013-10-03
Pic of CoolerMaster with 5.030GHz OC and pic of Ubuntu Shack :)lol

---

### Post by ventrical on 2013-10-03
Looks like my assignment will take over a year! :) lol

```

[Work thread Oct 3 12:00] Iteration: 190000 / 62406301 [0.30%].  Per iteration time: 0.213 sec.
[Comm thread Oct 3 12:23] Updating computer information on the server
[Comm thread Oct 3 12:23] Sending expected completion date for M62406301: May 19 2015
[Comm thread Oct 3 12:23] PrimeNet success code with additional info:
[Comm thread Oct 3 12:23] WARNING: Estimated completion date is more than one year away.  The assignment may be reassigned to another user after one year.
[Comm thread Oct 3 12:23] Done communicating with server.
[Work thread Oct 3 12:38] Iteration: 200000 / 62406301 [0.32%].  Per iteration time: 0.227 sec.

```

---

### Post by ventrical on 2013-10-03
I got my AMD64Athlon2X6000 so I have been working wth that. AMDs burn a little hotter than most .. so I  put an extra blower from a microwave oven on the case near the CPU heatsync in case of fan fail.  It really moves a lot of air and is really quiet.

  I am currently running the mprime torture test (3) and my CPU actually got cooler ;)

 Also zsyncing saucy beta amd64 and see if I can boost it higher.
Regards..

---

### Post by cariboo on 2013-10-03
Moved to Ubuntu, Linux and O/S chat as it really isn't specific to solving problems when running Saucy.

---

### Post by ventrical on 2013-10-04
.... ok... I zsynced the amd64 saucy iso beta, installed it on a USB using SDC and it will not boot up at this speed. It starts to boot but then it spits out verbose messages of kernel panic, not able to sync. So I will have to  down clock it  and then install saucy-desktop-amd64.iso beta on to a hard drive and see how it performs from here. The .iso Itself works great on an AMD64Athlon2X Dual 6000 .... whopp s.. I just figured it out .. that the current OC'ed machine is only 32 bit :) lol

Also .. just for the sake of validating that this is the problem I will try to boot the 32bit version USB on the same machine.

Regards..

*edit*

Yes .. the current processor I am using does not support 64bit. I have only one Cedar Mill Pentium 4 @ 3.40GHz that supports 64bit and 3 other 3.40GHz  that are non Cedar Mill  (80nm) that I will try but I doubt I will get the stability with the current processor I am using with those other processors.  Still .. I am interested on how saucy-desktop-amd64.iso works at over 5 GHz if I can get that high on those other processors.

Regards

---

### Post by ventrical on 2013-10-04
Thats the SL96J 651 Cedar Mill with 64bit. (65nm)

Regards..

---

### Post by ventrical on 2013-10-04
I lost two Cedar Mill 3.20GHz Pentiums whilst attempting to run the "live" session of saucy-desktop-amd64.iso @ 5.030GHz from a USB boot drive.  Once I reinstalled a new processor and downclocked I was able to get  the 64bit version running very nicely @ 4GHz so far at (80nm). The amd64bit version is much more stable (overclocked and at nominal - non cutting edge speeds). The 64bit "live" session is much more stable than the 32bit version but I have not  found too many problems with the i386 beta with he exception that is had obsoleted some  graphical adapter cards.

  The lesson learned here is  - do not try to run an amd64 saucy live session at a high clock rate but it is OK to run the i386 32bit version "live". Downclock first and then install amd64 but version and then upclock.

  Fortunately  for me I have lots of surplus Pentium Cedar Mills and Celerons to work with.

  A brief summary so far is that  both the i386 and amd64 bit version of Saucy Beta are working exceptionally well at high speeds and in the live sessions. I know many others are having problems and difficulties but on my power machines they are working well at both overclocked and nominal speeds.

 Don't try these experiments unless you have extra MoBos, processors and an enthusiasm to swap parts and experiement. If you want to push Ubunu to the edge, get some extra parts, otherwise it is better to keep safe and cozy at nominal and standard speeds.

Regards..

---

### Post by grahammechanical on 2013-10-05
Just as I was thinking that it was safe to get into the water along comes Jaws! :)

Ventrical, what breaks which? Does the over-clocked processor run the live session so fast that it causes a go faster loop, or in some way increases the heat output? I can understand instability showing up in an OS. I can also understand an over-clocked CPU burning out without any OS loaded. What is happening here?

I have always thought over-clocking to be scary, scary. My Asus P5B has over-clocking functions as part of the BIOS, It came with Windows based over-clocking utilities but, as to be expected, no Linux over-clocking utilities. And that is what scares me the most. The knowledge that a hard shutdown is the only way to protect the electronics but by then it would be too late. Psensor gives temperature reading for motherboard, CPU, Core1 and Core2 but I would not know when things had gone too far. And there would be no way of resetting from inside the OS.

Regards.

---

### Post by ventrical on 2013-10-05
Hi Grahammechanical,

I have an older ASUS P5AD2-e Deluxe which is very versatile and was built specifically for overclocking (and overclock protect) . 

 You ask a pointed question with a certain degree of difficulty that I may no be able to asnwer if full. What happened here is that the <already installed current saucy-desktop-amd64.iso on USB> was inserted into ver2.0 USB port while machine was OFF.   I booted with the Plop bootloader CD in the CD drive. All went well at first and then  a column of verbose errors came up with the final error refering to 'kernel panic - not able to sync.. etc'. The USB drive was not persistive  (discard on shutdown) so there is no log of the event.

  I then proceeded to hard shutdown (and it did as it was locked up at that point) and when I restarted all I got was the greenlight and the fans going and the CD light constanly on.  I fanagled a few things .. and nothing .. no boot.

 I assumed I flipped the processor and , with all the enthusiasm in the world. I put in another processor without downclocking  in BIOS first.  I got the same error message about kernel and sync and then .. no boot.  Fortunately for me I have about 15 extra lga775s ready processors of varying types so it is no sweat. I finally cleared the CMOS and put in a new processor Pentium 3.40GHz (80nm) 64bit instruction set with HTT, then booted normally and installed the saucy-desktop-amd64.iso  Ubuntu on a sideX side to hdd. Went without a hitch.  Now I can overclock with no ill effects.

What happened?

  I assume that the 64bit image's first order of buisness is to attempt to determine the Intel/AMD 64bit Instruction set capability. At 5.030 GHz I am again assuming that there was a power surge to some part of the processor  that  now prevents it from being detected (and that perhaps the processor may still be good on another machine -yet to be determined)

 I see your ASUS board is Celeron D and Pentium 4 ready with lga775. If you are apprehensive about overclocking your Dual Core I would try and get some single core Celeron Ds 3.20 GHz of Pentium 3.20GHz Cedar Mill. The Pentium 4 3.20GHz (Cedar Mill) are 64 bit and it is that processor that I was able to get the 5.030HGz OC. (Also on the Celeron D 3.20GHz single thread 32bit (no 64bit)

> 
Ventrical, what breaks which? Does the over-clocked processor run the  live session so fast that it causes a go faster loop, or in some way  increases the heat output?

I think there was a surge  of heat at bootup when detecting for 64bit instruction set.  I  do not think it is OS related at all.. just that the OC was so high  in BIOS.. however .. these are just my preliminary declarations that I have not documented.

btw .. in my searches there was an fsbcontrol for Linux (almost like the windows Program) but I doubt it will work on saucy. CPU-G will not work on saucy either <but will work on Precise> (CPU-G linux is a CPU-Z like GUI application to tell you info about your processor.)

There is no physical damage to the CPUs in question that can be identified visually. Sometimes CPUs can 'lock' just like some PCI cards can lock. The only way to unlock them (it could be a locked undocumented interupt vector eg) is to remove and then replace the card. I am going to try a process using tin foil on one of the CPUs that is no longer being detected (that means short out the processor contacts) with the intention of unlocking and unidentified interupt on the chip .

Thanks for your participation and asking these questions - got me thinking :) lol

 I wouldn't worry about sharks with an Asus MoBo.  :)

regards..

---

### Post by ventrical on 2013-10-05
I think there is a bug with lm-sensors with certain cpus. It gives a false Power Temperature at certain times when up_clocking. Not much can survive 251degrees C and I checked all my components (by hand after shutdown and ground_out) and they are not even warm.

---

### Post by ventrical on 2013-10-05
This is what I mean .. dead bugs that never get any attention.

[https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/575420](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/575420)

---

### Post by ventrical on 2013-10-05
> **grahammechanical said:**
> Just as I was thinking that it was safe to get into the water along comes Jaws! :)

Regards.

Enjoy! :) lol

[URL="http://www.lm-sensors.org/"]http://www.lm-sensors.org/

> 
**September 5th, 2013: Hardware breakage reported ** Over the past few months, we had several reports of sensors-detect causing **serious trouble**  on recent hardware (most notably laptops.) We still don't know what  exactly is happening, and while it might be reversible, we don't know  how, so in practice this is equivalent to the hardware itself being  broken. The symptoms are that the display starts misbehaving ([/URL][ wrong resolution]("http://lists.lm-sensors.org/pipermail/lm-sensors/2012-April/035847.html") or [ wrong gamma factor]("http://lists.lm-sensors.org/pipermail/lm-sensors/2013-August/039810.html").)  We have mitigated the risk by changing the default behavior of  sensors-detect to no longer touch EDID EEPROMs and then to no longer  probe graphics adapters at all unless the user asks for it. We urge  maintainers to **backport changesets [r6040]("http://www.lm-sensors.org/changeset/6040") and [r6084]("http://www.lm-sensors.org/changeset/6084")** to all Linux distributions which are still shipping lm-sensors 3.3.2 or older. Versions 3.3.3 and newer are not affected. [URL="http://www.lm-sensors.org/"]
[/URL]

---

### Post by ventrical on 2013-10-05
Well... lo and behold I did my tin-foil proceedure and my 641-SL9KF Pentium 3.20GHz Cedar Mill is back up and running ! But now the lm-sensors is reporting incorrectly:

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.32 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.62 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.61 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.25 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4166 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +16.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +45.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +35.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

somewhat like cariboo had in his bug report.... cpu cannot be that cool.

  Back up now to 5 GHz and test that 64bit install. maybe it is a software bug.  This same kind of problem used to happen with the HIDs on the older Dells. Scanner or Printer software  and ethernet cards would lock the whole system down due to the software locking interups on startup or shutdown.

Regards..

edit..


 It's working just awesomely at 4.8GHz on amd64bit.

```

ventrical@ventrical-asusOC:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.62 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.61 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4141 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +10.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-asusOC:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4885 MHz
ventrical@ventrical-asusOC:~$ uname -a
Linux ventrical-asusOC 3.11.0-11-generic #17-Ubuntu SMP Tue Oct 1 19:42:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-asusOC:~$ 

```

---

### Post by ventrical on 2013-10-05
Back up to 5.030 GHz on 32bit install. Will not go stable at this speed on amd64bit. At 4.8GHz , 64bit works exceptionally well.
 Break time :) lol

---

### Post by grahammechanical on 2013-10-06
I have Psensors installed. It gives real time readouts and has an alarm function based upon chosen high and low thresholds. I thought that Psensors was making use of lm-sensors but lm-sensors was not installed. So, it might be possible to use Psensors as a cross check on what lm-sensors is saying.

lm-sensors gives some min, max and high, critical numbers which should prove useful in keeping a watch on what psensors is showing. The install of lm-sensors recommended installing some other utilities, fancontrol, senord, read-edid and i2c-tools. I can guess what a couple of them do and i think the read-edid was the utility being referenced in that report from the lm-sensors web site.

I am going to approach this from the point of view of the ordinary user doing a bit of over clocking tinkering but not wanting to break anything. Which is exactly what I am. I do take your point about having a spare CPU. That is the advantage of having hardware that is well behind the crest of the wave. Stuff that was once expensive is now, possibly, reasonably priced.

Oh, lm-sensors is giving me a CPU critical temperature of +95%. Ah, but what happens if I over clock? That is the temptation. I think I will start off with what Asus refers to as its BIOS Non-delay Overclocking System (N.O.S.) feature. It intelligently determines the system load and automatically boosts the performance for the most demanding tasks. Do I hear a chicken squawking? :)

Regards.

---

### Post by ventrical on 2013-10-06
> **grahammechanical said:**
> ...That is the advantage of having hardware that is well behind the crest of the wave. Stuff that was once expensive is now, possibly, reasonably priced.

Oh, lm-sensors is giving me a CPU critical temperature of +95%. Ah, but what happens if I over clock? That is the temptation. I think I will start off with what Asus refers to as its BIOS Non-delay Overclocking System (N.O.S.) feature. It intelligently determines the system load and automatically boosts the performance for the most demanding tasks. Do I hear a chicken squawking? :)

Regards.

  I have the N.O.S. feature also but depending on the type of chip you are using you may not get high end results. Better safe than sorry ! :) lol.. As ronac used to say ... "If it ain't broke - don't fix it!".. lol 

 I live in an industirial city and we have huge recycling  shops about so a lot of stuff get shipped here first.  They have  Saturday garage sales and so I can get loads of Pentiums, Celerons and Dual Cores for mostly next to nothing.  The trick is you want to get the LGA 775  Cedar Mill 3.20GHz Pentiums or Celerons. Those are the ones that can OC to 5.GHz with cool temps (on air only).. so it is very economic. I guess this whole topic , really, is about Ubuntu economics and how to survive the comming tranasitions as a beta tester without spending too much hard earned money and newer form-factors which Overclocking Abilities are far too contrite and really don't allow any freedom to experiement - mostly only that specified by the manufacturer so the whole FOSS concept is nipped at the bud right there - thats why I say .. keep your eyes open for older mo-boards in the PC hack shops around you. You will never know what you can get for $5 bucks now-a-days with everybody dumping their desktops for usless slates. Yu might even end up with an ES (engineering sample) that had unlocked multiplier ..etc.. the sky is the limit with some of the older Pentiums... plus I am having a riot .. I mean .. real fun...!!:):)  Running saucy-desktop-amd64 installed on hdd at 4.8GHz on a single core, HTT showed me a whole different dimension of how fast Ubuntu can work on an old  40GB SATA1 hdd!  I look at is as a way to compete with the competion in an economic fashion and still have  the snappy and effervescent Unity and Gnome-Flashback DEs running with virtual flawlessness.

 There is nothing  chicken about  running your processors in  conservative manner if you do not have the surplus parts to spare. Gather up some cheap, old parts first .. and then the chicken will grow eagle's wings ! :)lol


Regards..

---

### Post by ventrical on 2013-10-11
I am not trying to bump, but, I received this very weird message during a reboot. Sorry I didn't capture it .. it went something like this:

kernel panic
 system halted 
 permission denied
  You do not have the required License...

And that was with fully updated 13.10.

Regards..

---

### Post by ventrical on 2013-10-14
I did have some regression while doing an update/upgrade at 5GHz. But is was easlily recoverable. Still.. it should be stable at the speed. Still running cool though. 

 On a side note I had a 3.40 Pentium 4  for dinner.  I was doing this swap on another machine .. just experimenting .. and there was this huge cable I had to move out of the way. Unfortunately the cable sort of rubbed up against the CPU fan.  Well.. you're not going to believe this but I actually set the CPU Fan Fail alarm in the BIOS. So when I booted up I was getting this siren that sounded like an Olde English policecan  Bee doo Bee  doo... etc.. and I just  looked at it puzzled until I smelled smoke ... ahhhh ... finally  ... :) lol

edit:

Wrong assumption. CPU not busted.. just overheated. The KVM locked up and gave the appearance that the CPU was borked.

---

### Post by ventrical on 2013-10-23
Just putting up notes that I switched over to trusty.

CPU Temperature:    +34.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +15.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +35.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5031 MHz
ventrical@ventrical-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
ventrical@ventrical-System-Product-Name:~$

---

### Post by ventrical on 2013-10-23
Trusty is actually running 5 - 7 degrees C cooler (on air) than saucy was with normal activity.

Recent Torture Test on saucy:

Type of torture test to run (3): 3

Accept the answers above? (Y): y
[Main thread Oct 17 11:57] Starting workers.
[Work thread Oct 17 11:57] Worker starting
[Work thread Oct 17 11:57] Worker starting
[Work thread Oct 17 11:57] Setting affinity to run worker on logical CPU #2
[Work thread Oct 17 11:57] Setting affinity to run worker on logical CPU #1
[Work thread Oct 17 11:57] Beginning a continuous self-test to check your computer.
[Work thread Oct 17 11:57] Please read stress.txt.  Hit ^C to end this test.
[Work thread Oct 17 11:57] Beginning a continuous self-test to check your computer.
[Work thread Oct 17 11:57] Please read stress.txt.  Hit ^C to end this test.
[Work thread Oct 17 11:57] Test 1, 7800 Lucas-Lehmer iterations of M9961473 using Pentium4 type-0 FFT length 512K, Pass1=512, Pass2=1K.
[Work thread Oct 17 11:57] Test 1, 7800 Lucas-Lehmer iterations of M9961473 using Pentium4 type-0 FFT length 512K, Pass1=512, Pass2=1K.
[Work thread Oct 17 12:02] Test 2, 7800 Lucas-Lehmer iterations of M9961471 using FFT length 512K, Pass1=256, Pass2=2K.
[Work thread Oct 17 12:02] Test 2, 7800 Lucas-Lehmer iterations of M9961471 using FFT length 512K, Pass1=256, Pass2=2K.
[Work thread Oct 17 12:06] Test 3, 7800 Lucas-Lehmer iterations of M9837183 using Pentium4 type-0 FFT length 512K, Pass1=512, Pass2=1K.
[Work thread Oct 17 12:06] Test 3, 7800 Lucas-Lehmer iterations of M9837183 using Pentium4 type-0 FFT length 512K, Pass1=512, Pass2=1K.
[Work thread Oct 17 12:11] Test 4, 7800 Lucas-Lehmer iterations of M9737185 using FFT length 512K, Pass1=256, Pass2=2K.
[Work thread Oct 17 12:11] Test 4, 7800 Lucas-Lehmer iterations of M9737185 using FFT length 512K, Pass1=256, Pass2=2K.
[Work thread Oct 17 12:15] Self-test 512K passed!
[Work thread Oct 17 12:15] Test 1, 800000 Lucas-Lehmer iterations of M172031 using Pentium4 type-1 FFT length 8K, Pass1=32, Pass2=256.
[Work thread Oct 17 12:15] Self-test 512K passed!
[Work thread Oct 17 12:15] Test 1, 800000 Lucas-Lehmer iterations of M172031 using Pentium4 type-1 FFT length 8K, Pass1=32, Pass2=256.
[Work thread Oct 17 12:20] Test 2, 800000 Lucas-Lehmer iterations of M163839 using Pentium4 type-1 FFT length 8K, Pass1=32, Pass2=256.
[Work thread Oct 17 12:21] Test 2, 800000 Lucas-Lehmer iterations of M163839 using Pentium4 type-1 FFT length 8K, Pass1=32, Pass2=256.
[Work thread Oct 17 12:25] Test 3, 800000 Lucas-Lehmer iterations of M159745 using Pentium4 type-1 FFT length 8K, Pass1=32, Pass2=256.
[Work thread Oct 17 12:26] Test 3, 800000 Lucas-Lehmer iterations of M159745 using Pentium4 type-1 FFT length 8K, Pass1=32, Pass2=256.
[Work thread Oct 17 12:33] Self-test 8K passed!
[Work thread Oct 17 12:33] Test 1, 6500 Lucas-Lehmer iterations of M11285761 using type-2 FFT length 576K, Pass1=384, Pass2=1536.
^C[Main thread Oct 17 12:34] Stopping all worker threads.
[Work thread Oct 17 12:34] Torture Test completed 6 tests in 37 minutes - 0 errors, 0 warnings.
[Work thread Oct 17 12:34] Torture Test completed 7 tests in 37 minutes - 0 errors, 0 warnings.
[Work thread Oct 17 12:34] Worker stopped.
[Work thread Oct 17 12:34] Worker stopped.
[Main thread Oct 17 12:34] Execution halted.

Hit enter to continue:

---

### Post by ventrical on 2013-11-11
The current 3.12.0-2 kernel is allowing for more stable operation at high speeds and still cooler temps with air.

I was getting errors previously in Unity at speeds above 5.030 GHz but now, at;

```
 
ventrical@ventrical-beta:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 5062 MHz

```

..Unity and lightdm are loading very stable and I did not have to raise vCore and am able to keep that at lower values ... so I will attempt a higher overclock :)

 ```

ventrical@ventrical-beta:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.53 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.62 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.60 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4090 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +34.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +33.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +15.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +35.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-beta:~$ 

```

---

### Post by ventrical on 2013-11-11
I'm not sure what the kernel devs did  but this is the highest stable Unity/Lightdm yet on this machine !

```

ventrical@ventrical-beta:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5110 MHz
ventrical@ventrical-beta:~$ 

```

---

### Post by Werne on 2013-11-11
Haven't tried overclocking on Trusty yet, I'm still keeping my FX 8320 @4.6GHz, 1.404V like I did on Saucy. If Trusty drops the temps a bit, I may go over that since my AC Freezer 13 is not doing a very good job (54C max under full load @4.6GHz, 1.404V while it's 59C max @4.8GHz, 1.428V and CPU starts throttling). It's a budget cooler after all, I'd get water cooling but the radiator has trouble fitting in my case (ATX midi tower). Stock cooler is out of the question, that thing throttles when undervolted to 1.176V on stock speeds without turbo.

I can keep the temps down if I disable PWM but then the CPU fan gets loud, I might try raising the PWM curve instead to keep the noise down on idle. 1.428V (stock turbo voltage) would be tops though, can't afford a new CPU if I fry this one and I doubt my cooler would take the increase in power consumption. Ugh, I really need a new cooler.

Anyway, will try and see how far can I push this thing on Trusty, hope it drops temps a bit so I don't fry the bloody thing. It proved proved really good so far and as a performance test just for the hell of it, FX 8320 @4.6GHz compiles 3.11.6 kernel+headers in 11m 22.493s (compiled in a 4GB tmpfs) as compared to 14m 46.339s on stock 3.5GHz. That's one hell of a performance increase.:-D

By the way, those P4s overclock like crazy, I had an old Northwood that was chugging at 5.4GHz for about 2 years, died after I got it to some 6GHz. And C2Ds are also good, my old E4500 was running perfectly @4.42GHz, 1.524V. Ivy Bridge and Haswell suck though, they overheat fast.

---

### Post by ventrical on 2013-11-11
@werne

  I am having trouble with the older AMD overclocks. Gets hot really fast.  That is athlon64x2 5000 and 6000.

 So far, so good here @5.160. I had to raise the vCore to  1.5375. I'm trying for 5.2GHz and will be happy with that.

Stock Coolermaster here. I really don't mind the fan at all.

 Let me know if you get better performance with this kernel as I do.


Regards.

Oh yeah .. haswell and ivybridge.. Intel put some bad thermal paste under the IHS so a lot of modders are delidding them, repasting them and then overclock. Much better performance.

---

### Post by dannyboy79 on 2013-11-11
i have an E4300 which i OC'd to 2.4Ghz from 1.8Ghz using the BIOS (AsRock 775dual-VSTA), how are you guys able to OC from within the OS?

---

### Post by ventrical on 2013-11-11
At this point I also am doing overclocks from the BIOS. There are some linux programs that will manipulate FSB for overclock but I hadn't the time as of yet.

---

### Post by Werne on 2013-11-12
> **dannyboy79 said:**
> i have an E4300 which i OC'd to 2.4Ghz from 1.8Ghz using the BIOS (AsRock 775dual-VSTA), how are you guys able to OC from within the OS?
I use BIOS for that, software overclocking is not as reliable, I killed my first i5 3570K that way. I set the VCore to 1.484V to reach 5GHz and the program set it to 1.568V to compensate for VDrop, but it didn't know I used extreme VCore load line calibration which overvolts the life out of it, so it got deep-fried after about 3 seconds at 1.642V. Bummer.



And I did get somewhere on Trusty, didn't help with temperatures but ripping off the side panel, disabling PWM and putting another fan to blow on NB did lower them, dropped temps to 49C under load at 1.404V since I got another 200RPM out of the CPU fan. Can't go over to 1.428V though since it starts throttling, so I took advantage of BCLK - pumped the NB voltage by 0.150V and raised BCLK to 240MHz to have breathing space. Set the multiplier to x20 and lowered BCLK to 231MHz reaching 4.62GHz across 8 cores, I could likely hit 5GHz if I disable some cores but that ain't fun, I want the full multi-threading power of this thing. Also disabled power states which yaps about a firmware bug, it's a known issue and affects nothing so I don't care.

Passed a 3 hour mprime stress test, I'm satisfied. 20MHz ain't much but it's something.

Frequency:
```
werne@ubuntu-devel:~/build/kernel/linux-3.11.6$ cat /proc/cpuinfo|grep 'cpu MHz'
cpu MHz        : 4620.899
cpu MHz        : 4620.899
cpu MHz        : 4620.899
cpu MHz        : 4620.899
cpu MHz        : 4620.899
cpu MHz        : 4620.899
cpu MHz        : 4620.899
cpu MHz        : 4620.899
```

I don't know why but dmidecode and lshw report 4.0GHz freqency, as if I still have BCLK at 200. Only /proc/cpuinfo reports correct speeds. And something I hate is that sensors doesn't report VCore like it did on my old E4500. :(

Oh, and just for the hell of it...
```
werne@ubuntu-devel:~/build/kernel/linux-3.11.6$ time fakeroot make-kpkg -j8 --initrd --revision=1.werne kernel_image kernel_headers

<removed several thousand lines of output>

real    9m33.356s
user    42m41.876s
sys    5m22.252s
```

I was hoping to get a compile time around 11 minutes, but 9m 33s is much better, seems disabling power states gives one hell of a boost. :D

---

### Post by ventrical on 2013-11-12
Thats a more than decent overclock.  I have the Mother Board ..etc.. and just have to get my i7 now... like as if I am not already in the poorhouse ... :) lol

---

### Post by Werne on 2013-11-13
> **ventrical said:**
> Thats a more than decent overclock.  I have the Mother Board ..etc.. and just have to get my i7 now... like as if I am not already in the poorhouse ... :) lol
It's an average overclock, I wouldn't call it decent. And yeah, those i7s are bloody expensive, around here they cost over 500$, an i5 3570K is 350$, and Intel i7 Extreme is over 1200$. Not like I see the purpose of those, same as I don't see a purpose for an AMD octa-core, except if you get them on discount like I got mine or you actually need one for work or something.

And by the way, most Haswell i7s I've seen (by "seen" I mean "had a chance to OC") overclock poorly, I tried four and most I got out of them was 4.47GHz out of one, others were below 4.4GHz because they were doing the bluescreen if raised further (Windows machines, haven't seen a system crash since I switched to Linux). And they were overheating like crazy before TIM replacement, the one that hit 4.47 was overheating on 4.24GHz with Corsair H100i.

Ivy Bridge can OC well once you replace the TIM though, I've seen several getting near 5GHz on liquid, two even went over. Another good overclocker is an AMD A10-6800K, most I've seen were capable of going over 5GHz without breaking a sweat, a friend of mine yanked one up to 5.7GHz, 1.486V on multi alone (yeah, he brute-forced it). I'd bet my left leg that thing could've hit 6GHz with further fiddling but he chickened out. I think the modules used in A10-6800K are the same ones used in FX 9570/9590 with an addition of a graphics chip on the die, but I'm not entirely sure.



And something I didn't have time to mention when I was replying to dannyboy.
> **dannyboy79 said:**
> i have an E4300 which i OC'd to 2.4Ghz from  1.8Ghz using the BIOS (AsRock 775dual-VSTA)
By the looks of it, that mobo seems like a cross-breed between a low-end ASUS and mid-range Gigabyte, which means it may have VCore, RAM and NB voltage adjustment, along with RAM latency and ratio options as well. Not sure, never used an ASRock mobo, I only ever used ASUS and Gigabyte boards.

Anyhow, if you hit a wall at a low frequency increase like 1.8 > 2.4GHz, it can be that RAM can't take it and you need to loosen up the latencies and increase voltage (DDR2 is 1.8-2.1V and DDR3 is 1.5-1.65V or 1.25-1.35V for low-voltage RAM). Also could be that RAM can't take the frequency increase at all, so you can adjust the ratio, happens with low-end RAM modules. Calculating how far you need to loosen up the latencies is easy, if we take my DDR3-1333 Transcent JetRam with 9-9-9-24 latencies as an example and want it at 1600MHz, we calculate like so:

Calculation: (9/1.333)*1.600=10.8 ~= 11    (24/1.333)*1.600=28.8 ~= 29
Latency for 1600: 11-11-11-29 loose or 10-11-10-28 aggressive

Replace 1.600 with the current RAM frequency of yours of course. If it has a memory multiplier, you can lower that below stock frequency instead of fiddling with latencies so you can continue without RAM getting in the way.

Another thing, overclocking through FSB requires Northbridge overclocking as well, not just CPU. First thing I do when overclocking a Core 2 (or any CPU with locked multi) is lower the CPU and RAM multipliers to minimum, push the FSB and NB voltage as far as it can go (running Prime95 each time I increase frequency), return FSB to stock while keeping the NB overvoltage, raise CPU multiplier to desired value lower than stock (leave RAM at minimum), push the FSB and raise VCore on benchmark failure. Much easier to overclock when you know only one thing can fail, and that one thing is the CPU which needs more volts. If I can't reach max FSB from the first run, I can tune NB voltage down since it's useless to keep it high if not needed, and adjust the rest. Then RAM comes into play, desired is the same or nearest possible frequency to stock.

NB can take up to 0.125V increase in voltage without a problem, over that becomes risky unless you have a dedicated NB fan like me. Also, I wouldn't recommend pushing a C2D over 1.45V if you're inexperienced, unless you intend to replace your PC in the near future. RAM, keep it as close to stock frequency as possible, you get maybe 2-3% by raising RAM frequency since latency plays a big role in RAM speed too. And finally, make sure only one thing can crap out at a time or you'll become overwhelmed with setting changes, then you can easily mess up and destroy your hardware.

---

### Post by ventrical on 2013-11-13
> **Werne said:**
> It's an average overclock, I wouldn't call it decent. And yeah, those i7s are bloody expensive, around here they cost over 500$, an i5 3570K is 350$, and Intel i7 Extreme is over 1200$. Not like I see the purpose of those, same as I don't see a purpose for an AMD octa-core, except if you get them on discount like I got mine or you actually need one for work or something.



Same price here up in Canada.

  I have a 2.4GHz Core2Duo Intel DQ965GF machine but with zero overclock capbilities in BIOS. (I am tempted to try my 3.0GHz Core2Duo on my 1155 as the current G630 in there has a locked FSB and locked multi (what a pain) but the BIOS has all the overclocking ready gear -to- go!.)

My two other boards are the ASUS P5AD2-E for Intel chips (non-dual core operational 775 socket) and ASUS AVM-2M for AMD CPUs x2. The p5AD2-E is a beast with 3.2 Celerons with no HT. I can run over 5GHz all day and night on air only.

  Haven't had a chance to OC IvyBridge. By the sounds of it , doesn't sound like much fun. :) lol

  Thanks for sharing you stats and experience.  I am going to try for 6GHz on air alone on a non Cedar Mill (80nm lithography) and set a cut off temp of 80C and see what happens. I get 'chicken legs' too , especially with that legacy MoBo.. but Ubutnu (and I am assuming  the new kernel) make it worth the try.

  Also .. at times I get this false reading from PWR when running Celerons. It reports that the temp is 207C .. or there about... yet none of the components on the mobo are even warm .

 Be nice if I had the proprietary 711MHz ddr2 for that board .. but ..I'm using 800 and setting mem freq at 400MHz (lowest) . Also be nice to have some 1066ddr2 but good luck trying to find that at the local shops :)

---

### Post by Werne on 2013-11-13
> **ventrical said:**
> Intel DQ965GF machine but with zero overclock capbilities in BIOS. . (I am tempted to try my 3.0GHz Core2Duo on my 1155 as the current G630  in there has a locked FSB and locked multi (what a pain) but the BIOS  has all the overclocking ready gear -to- go!.)
I hate those boards. Quality? Awesome. Overclocking capability? Non-existent. And you do know you can't use a Core 2 Duo on a 1155 mobo, right?

By the way, that G630 can be OCd if you can modify BCLK but watch it with that one, you can destroy more than just the CPU/mobo with BCLK (like graphics card, HDD, etc). Intel systems are especially sensitive to BCLK overclocks where even 4-5% can destroy components or make you fail to boot, AMD systems are not as sensitive, I raised BCLK by 15% and it works just fine, I can even go higher. Also, it's likely that mobo is locked as well depending on the chipset, Intel locks FSB/multi on low-end mobos, they're mean.

> **ventrical said:**
> Thanks for sharing you stats and experience.  I am going to try for  6GHz on air alone on a non Cedar Mill (80nm lithography) and set a cut  off temp of 80C and see what happens. I get 'chicken legs' too ,  especially with that legacy MoBo.. but Ubutnu (and I am assuming  the  new kernel) make it worth the try.
No problem, I've been crazy about overclocking since I got my first Pentium II and I learned quite a bit since then. If I recall correctly, cause it's been a while since I OCd a Cedar Mill, a P4 641 can take up to 75C constant without any permanent damage to the die, with temperature bursts up to 83-84C, so 80C cutoff is good. As for voltage, I think the max that thing can take is somewhere around 1.64V. It's a persistent little bugger, lives fast and dies in a blaze of glory. :wink:

As for chicken legs, I feel that way when I overclock my own CPU. But if overclocking some old one, or someone else's? Nope, then I torture it until it explodes. :twisted:

> **ventrical said:**
> Also .. at times I get this false reading from PWR when running  Celerons. It reports that the temp is 207C .. or there about... yet none  of the components on the mobo are even warm .
It's a know thing with the sensors. I had an ASUS P5KPL-AM mobo once, the CPU sensor on it would sometimes report the CPU temperature of over 18,000C. I know stock coolers are bad, but I never thought they were that bad. :p

Oh, and when it comes to RAM, I don't know about Canada but there's plenty of DDR2-1066 around here in Croatia, I've even seen brand-new kits in the store. I've never even heard of the DDR2-771 though, must've been some special-purpose RAM or something.:confused:

---

### Post by ventrical on 2013-11-13
> **Werne said:**
> I hate those boards. Quality? Awesome. Overclocking capability? Non-existent. And you do know you can't use a Core 2 Duo on a 1155 mobo, right?

By the way, that G630 can be OCd if you can modify BCLK but watch it with that one, you can destroy more than just the CPU/mobo with BCLK (like graphics card, HDD, etc). Intel systems are especially sensitive to BCLK overclocks where even 4-5% can destroy components or make you fail to boot, AMD systems are not as sensitive, I raised BCLK by 15% and it works just fine, I can even go higher. Also, it's likely that mobo is locked as well depending on the chipset, Intel locks FSB/multi on low-end mobos, they're mean.


No problem, I've been crazy about overclocking since I got my first Pentium II and I learned quite a bit since then. If I recall correctly, cause it's been a while since I OCd a Cedar Mill, a P4 641 can take up to 75C constant without any permanent damage to the die, with temperature bursts up to 83-84C, so 80C cutoff is good. As for voltage, I think the max that thing can take is somewhere around 1.64V. It's a persistent little bugger, lives fast and dies in a blaze of glory. :wink:

As for chicken legs, I feel that way when I overclock my own CPU. But if overclocking some old one, or someone else's? Nope, then I torture it until it explodes. :twisted:


It's a know thing with the sensors. I had an ASUS P5KPL-AM mobo once, the CPU sensor on it would sometimes report the CPU temperature of over 18,000C. I know stock coolers are bad, but I never thought they were that bad. :p

Oh, and when it comes to RAM, I don't know about Canada but there's plenty of DDR2-1066 around here in Croatia, I've even seen brand-new kits in the store. I've never even heard of the DDR2-771 though, must've been some special-purpose RAM or something.:confused:


 Yes .. I'll get the specs from the manual.  It ( 771) is specific to that MoBo. I'll have to double check that.
 

> 
No problem, I've been crazy about overclocking since I got my first  Pentium II and I learned quite a bit since then. If I recall correctly,  cause it's been a while since I OCd a Cedar Mill, a P4 641 can take up  to 75C constant without any permanent damage to the die, with  temperature bursts up to 83-84C, so 80C cutoff is good. As for voltage, I  think the max that thing can take is somewhere around 1.64V. It's a  persistent little bugger, lives fast and dies in a blaze of glory. :wink:


Got 4 of those. Fried two already (forgot to plug the fan in on one - geesh). Currently I have the 3.20 Cedar Mill and that is giving me a solid 5.130GHz/ I can install programs from Software Center and it won't crash :) lol

  Thanks .. you made my day  :)

---

### Post by ventrical on 2013-11-13
It is 711 MHz ... apologies.. my bad..

> 
Visit the ASUS website for the latest DDR2-711 MHz (FSB 1066)/
DDR2-600 MHz (FSB 800)/DDR2-533 MHz (FSSB 1066/800) Qualified
Vendors List.
ASUS P5AD2-E Delu..



---

### Post by ventrical on 2013-11-14
5.2GHz wall

I get to this point, after trying to adjust all the bells and whistles, and still get:

```

kernel panic not syncing:VFS: unable to mount root fs on unknown -block (0,0)

```

I tried switching hdds but get the same problem.  GRub is loading, then , in recovery mode all loads up well until the final kernel panic. So naturally the CPU is going to fast to catch that hook. I tried to adjust FSB Termination volts and Chipset Volts, even pushed vCore to 1.7v... hmmmm .. it could be the hyperthread. I'll try diabling that , but  then this is not a stable overclock.

  Then again, mabey there are limits to the software also.

---

### Post by ventrical on 2013-11-14
I am now using the Grub Rescue 'Live" CD and it is overclocking just fine at:

```

user@debian:~$ sensors 
bash: sensors: command not found
user@debian:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 5207 MHz
user@debian:~$ 


```

using Mozilla's Ice Weasel.

So there is obviously a power problem vs a kernel problem when using standard hdd while overclocking the trusty kernel.

```

user@debian:~$ uname -a
Linux debian 2.6.32-5-486 #1 Sat Jun 11 19:49:29 UTC 2011 i686 GNU/Linux
user@debian:~$ 


```
which is the GRub rescue  live' CD kernel.

---

### Post by Werne on 2013-11-14
That kernel... I think GRUB Rescue uses Debian Squeeze as base. Could be that a stripped-down system like that one can take more than a complex system like Trusty, less things that could go wrong. And maybe there was some change in Linux 3.12 that affects it somehow. Or could be that an older system like Squeeze is better optimized for old hardware. Don't know, but something is definitely not right.

Have you tried sifting through /var/log to find the leftovers from the aftermath? kern.log and syslog will likely contain the reason for the kernel panic and might help in finding a solution.

---

### Post by ventrical on 2013-11-14
> **Werne said:**
> That kernel... I think GRUB Rescue uses Debian Squeeze as base. Could be that a stripped-down system like that one can take more than a complex system like Trusty, less things that could go wrong. And maybe there was some change in Linux 3.12 that affects it somehow. Or could be that an older system like Squeeze is better optimized for old hardware. Don't know, but something is definitely not right.

Have you tried sifting through /var/log to find the leftovers from the aftermath? kern.log and syslog will likely contain the reason for the kernel panic and might help in finding a solution.

  Lots of voluminous  info there.  Nothing specific to kernel panic in either kernel.log or sys.log but some interesting stuff with rtkit-daemon  and some NVidia stuff. I might have to experiement with the PCIe frequencies a bit.

rtkit-daemon.. is that rootkit hunter? .. because I never installed it.

---

### Post by ventrical on 2013-11-14
> **Werne said:**
> That kernel... I think GRUB Rescue uses Debian Squeeze as base. Could be that a stripped-down system like that one can take more than a complex system like Trusty, less things that could go wrong. And maybe there was some change in Linux 3.12 that affects it somehow. .

Thing is , I am still able to squeeze and extra 100MHz out of the 3.12 kernel .... and have Unity 3D running smoothly where it would not run in the previous kernels .. so I would say that is progress. :)

---

### Post by Werne on 2013-11-15
> **ventrical said:**
> rtkit-daemon.. is that rootkit hunter? .. because I never installed it.
Huh, no rtkit-daemon in my Trusty, not sure how you got it. And 100MHz is progress, something is better than nothing.;) Did you manage to resolve the issue with kernel panics or are you still on it?



And I've finally succeded at dropping temperatures a bit, drilled a hole in the case and inserted a 92mm top fan for heat extraction. Reset BIOS and went from scratch, currently at 4.6GHz, 1.404V regular load line calibration by bruteforcing, sensors show a maximum temeprature spike of 45.1C. That means I can aim for 1.428V and higher, maybe I'll be able to hit 4.7GHz. Just have to wait for Trusty to update and I'll be back in BIOS, fiddling with this thing again.

EDIT: Finally, 4.72GHz @1.428V (Extreme LLC). Prime95 running for about 35 minutes now, still has to go another hour and a half, highest reached temperature is 47.6C. Looking good so far. :grin:

---

### Post by ventrical on 2013-11-15
> **Werne said:**
> Huh, no rtkit-daemon in my Trusty, not sure how you got it. And 100MHz is progress, something is better than nothing.;) Did you manage to resolve the issue with kernel panics or are you still on it?
:grin:

 I am still on it.  I am of the thinking that there may be a problem with the on-board LAN. I stripped the MoBo of all PCI  cards with exception of PCIe nVidia which has a freq control in BIOS for overclock. It seems when I go past 5.2GHz that the times it did boot up successfully the network indicator would drop from the panel. Also would not detect hdd ..etc.. so my next step is to disable the onboard lan and stick in a PCI ethernet card and see where it goes from there. Also, would be nice if I had 1066MHzDDR2 memory as I think the current 800MHz is just dropping out or not syncing right .(which would explain the kernel panic a little better. Of course , as you know . there are many other factors which I am exploring atm.

Regards..

---

### Post by ventrical on 2013-11-15
> **Werne said:**
> 
And I've finally succeded at dropping temperatures a bit, drilled a hole in the case and inserted a 92mm top fan for heat extraction. Reset BIOS and went from scratch, currently at 4.6GHz, 1.404V regular load line calibration by bruteforcing, sensors show a maximum temeprature spike of 45.1C. That means I can aim for 1.428V and higher, maybe I'll be able to hit 4.7GHz. Just have to wait for Trusty to update and I'll be back in BIOS, fiddling with this thing again.

EDIT: Finally, 4.72GHz @1.428V (Extreme LLC). Prime95 running for about 35 minutes now, still has to go another hour and a half, highest reached temperature is 47.6C. Looking good so far. :grin:

That's encouraging news  for that chip. I have a 'stack -cooler' on the bottom of the MoBo
where the CPU is and that helps in the cooling process too. The top fan is a smart idea as when we are running cooling on air it is very important to keep the ambient air going across the heat-pipes the same as ambient room temps, otherwise is starts to recycle air that is a higher temp then outside box ambient.

I'm back at it here ..

---

### Post by ventrical on 2013-11-15
Turned of HT, disabled SMART, disabled onboard LAN (yet I am still live) comming at you with a stable:

```

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5207 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

with

```


ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.62 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.59 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +42.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +33.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature: +255.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

obviously the Power Temp is a bug with lm-sensors (trusty) so I'll go back to an earlier version and see if I get the same bug with HT off.

Regards...

---

### Post by Werne on 2013-11-15
> **ventrical said:**
> I am still on it.  I am of the thinking that there may be a problem with the on-board LAN. I stripped the MoBo of all PCI  cards with exception of PCIe nVidia which has a freq control in BIOS for overclock. It seems when I go past 5.2GHz that the times it did boot up successfully the network indicator would drop from the panel. Also would not detect hdd ..etc.. so my next step is to disable the onboard lan and stick in a PCI ethernet card and see where it goes from there. Also, would be nice if I had 1066MHzDDR2 memory as I think the current 800MHz is just dropping out or not syncing right .(which would explain the kernel panic a little better. Of course , as you know . there are many other factors which I am exploring atm.

Regards..
Hmm, could be that the FSB affects the PCI-E frequency, I know BCLK affects HyperTransport and Northbridge frequencies. HT frequency increase is not a good thing, it controls Southbridge frequency and can destroy the storage drives if raised too high. My guess is that NB/SB communication is acting up, could be that one (or both) of those needs more power to keep everything in line.

As for the memory, did you try loosening up the latencies and/or upping the DRAM volts? That could help, some of those DDR2-800 will clock damn good with voltage increase and latency adjustments, I still have some old Crucial Ballistix DDR2-800 that I managed to push up to 1866MHz @2.20V, that's some fine RAM.

> **ventrical said:**
> That's encouraging news  for that chip. I have a 'stack -cooler' on the bottom of the MoBo
where the CPU is and that helps in the cooling process too. The top fan  is a smart idea as when we are running cooling on air it is very  important to keep the ambient air going across the heat-pipes the same  as ambient room temps, otherwise is starts to recycle air that is a  higher temp then outside box ambient. 
Yeah, I know. However, since I already had a well ventilated case (2x92mm push, 2x92mm pull) I thought I solved the issue. But since hot air goes up and my cooler is mounted so it blows upwards (can't mount it any other way except rotate it 180 degrees), I needed a fan to extract hot air from the above. Now the CPU is all nice and cool, reaching maximum temperature of 48.3C @1.428V. And the frequency is:

```
werne@ubuntu-devel:~$ cat /proc/cpuinfo|grep 'cpu MHz'
cpu MHz        : 4722.236
cpu MHz        : 4722.236
cpu MHz        : 4722.236
cpu MHz        : 4722.236
cpu MHz        : 4722.236
cpu MHz        : 4722.236
cpu MHz        : 4722.236
cpu MHz        : 4722.236
```

Nice, 4.72GHz across 8 physical cores, a 1.22GHz increase from stock. :cool: Might go compile the kernel and headers to see how fast this thing is, then I'll fiddle with BCLK a bit, try to milk all I can from this thing.

---

### Post by ventrical on 2013-11-15
So now I am running mprime torture test (3) and the Power Temp drops to:

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.54 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.61 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.60 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4017 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +45.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:   +5.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 


```

---

### Post by ventrical on 2013-11-15
> **Werne said:**
> Hmm, could be that the FSB affects the PCI-E frequency, I know BCLK affects HyperTransport and Northbridge frequencies. HT frequency increase is not a good thing, it controls Southbridge frequency and can destroy the storage drives if raised too high. My guess is that NB/SB communication is acting up, could be that one (or both) of those needs more power to keep everything in line.

As for the memory, did you try loosening up the latencies and/or upping the DRAM volts? That could help, some of those DDR2-800 will clock damn good with voltage increase and latency adjustments, I still have some old Crucial Ballistix DDR2-800 that I managed to push up to 1866MHz @2.20V, that's some fine RAM.


 Yes I had tried  driving up mem volts. It is working fine now with HT off (mem 2.00v) . I am going to bring it as high as I can with HT off and then troubleshoot from there.  Haven't touched latency adjust as of yet but that could be the problem also.

---

### Post by ventrical on 2013-11-15
Ok.. it appears that I broke through the wall at 5.287 GHz. I set FSB to 330 and upped vCore to 1.6125 and now I have the normal Power Temps again (without running mprime). I am going to mprime torture test for a bit and then try and up it some more..

```

Vcore Voltage:      +1.52 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.62 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.60 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +35.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5287 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by Werne on 2013-11-16
Nice, but make sure you have decent NB cooling, that thing can take high temps easily but it still needs to be cooled well, I have a dedicated NB fan even though I don't actually need one for now. And as I'm currently struggling this one, make sure your VRMs are cooled well.



When it comes to my OC, seems like I've hit a wall on the power front. While my CPU can operate on 4.72GHz @1.428V with the peak temperature of 45.6C, my GA-970A-UD3 is struggling with the increased power draw. The VRMs are starting to heat up like crazy so I'll either have to find a way to cool them down, or give up on reaching 1.456V and 4.8GHz. That means I have to invent a spot fan to blow on those, which shouldn't be that hard, I have spare AMD stock cooler fans that can spin at 4000RPM and plenty of aluminum plates to mount the fan on, should keep the VRMs adequately cooled once I position it right.

EDIT: inserted a 40mm 2200RPM fan for VRM cooling and replaced the fan which feeds air to NB with a 60mm 4400RPM fan from 939 socket CPU cooler. CPU got a 0.6C increase in temperature, likely due to the fact that the VRM fan is positioned in a crappy way, but it's nothing since CPU peaks out at 46.2C which is 15.8C below manufacturer maximum and 5.8C below the point at which it begins to throttle. And that allows me to go 1.456V, so I think I'll go fiddle with BIOS now. :D

---

### Post by grahammechanical on 2013-11-16
I have no intention of becoming such an extreme over clocker as both of you. But I might experiment a little. I have been looking for something that shows the CPU frequency in real time. And this thread has show me something that might be useful.

[http://ubuntuforums.org/showthread.php?t=2188234](http://ubuntuforums.org/showthread.php?t=2188234)

I have installed GkrellM and its CPU frequency plugin (gkrellm-cpufreq). It is in Synaptic. It shows a nice little GUI and once the cpu frequency plugin is enabled it also shows the on demand CPU frequency of both my cores. It might be useful for detecting over-speed which will lead to thermal runaway.

Regards.

---

### Post by ventrical on 2013-11-16
> **grahammechanical said:**
> I have no intention of becoming such an extreme over clocker as both of you. But I might experiment a little. I have been looking for something that shows the CPU frequency in real time. And this thread has show me something that might be useful.

[http://ubuntuforums.org/showthread.php?t=2188234](http://ubuntuforums.org/showthread.php?t=2188234)

I have installed GkrellM and its CPU frequency plugin (gkrellm-cpufreq). It is in Synaptic. It shows a nice little GUI and once the cpu frequency plugin is enabled it also shows the on demand CPU frequency of both my cores. It might be useful for detecting over-speed which will lead to thermal runaway.

Regards.

Thanks grahammechanial! Just what I've been looking for.  The Linux version of CPU-Z (which is a Windows based program )  :)lol  is CPU-G. It will run in Raring and Precise but not Saucy or Trusty.

cpu-g_0.9.0_i386.deb

so it is pretty well useless for testing Trusty.

 I'll also have to aquire some more Celeron 347s  (cedar mills) as I have only now a stack of 352s which have a hard time getting past 5GHz.

 Next , my plan to test trusty 64bit with new 3.12 kernel.

Regards..

---

### Post by ventrical on 2013-11-16
Got it to work but do not see where it reports cpu frequency.

  I'll try an overclock later.

Thanks again.

---

### Post by ventrical on 2013-11-16
> **Werne said:**
> Nice, but make sure you have decent NB cooling, that thing can take high temps easily but it still needs to be cooled well, I have a dedicated NB fan even though I don't actually need one for now. And as I'm currently struggling this one, make sure your VRMs are cooled well.



When it comes to my OC, seems like I've hit a wall on the power front. While my CPU can operate on 4.72GHz @1.428V with the peak temperature of 45.6C, my GA-970A-UD3 is struggling with the increased power draw. The VRMs are starting to heat up like crazy so I'll either have to find a way to cool them down, or give up on reaching 1.456V and 4.8GHz. That means I have to invent a spot fan to blow on those, which shouldn't be that hard, I have spare AMD stock cooler fans that can spin at 4000RPM and plenty of aluminum plates to mount the fan on, should keep the VRMs adequately cooled once I position it right.

EDIT: inserted a 40mm 2200RPM fan for VRM cooling and replaced the fan which feeds air to NB with a 60mm 4400RPM fan from 939 socket CPU cooler. CPU got a 0.6C increase in temperature, likely due to the fact that the VRM fan is positioned in a crappy way, but it's nothing since CPU peaks out at 46.2C which is 15.8C below manufacturer maximum and 5.8C below the point at which it begins to throttle. And that allows me to go 1.456V, so I think I'll go fiddle with BIOS now. :D


  I do most of my own mods also. All of the above .. you're right. Good advice! Thanks.

Regards..


btw .. with your VRMs running hot like that  then watch your caps (if they still have them on those MoBos). I even make my own heat syncs but that is intricate work. I had to shave and bore some fins on one of my CoolerMaster sinks so they don't bump up against a row of caps (which was not affected by the original heat sink for that machine.)

---

### Post by ventrical on 2013-11-16
> **grahammechanical said:**
> I have no intention of becoming such an extreme over clocker as both of you. But I might experiment a little. I have been looking for something that shows the CPU frequency in real time. And this thread has show me something that might be useful.

[http://ubuntuforums.org/showthread.php?t=2188234](http://ubuntuforums.org/showthread.php?t=2188234)

I have installed GkrellM and its CPU frequency plugin (gkrellm-cpufreq). It is in Synaptic. It shows a nice little GUI and once the cpu frequency plugin is enabled it also shows the on demand CPU frequency of both my cores. It might be useful for detecting over-speed which will lead to thermal runaway.

Regards.


Ok.. I figured it out ... there is the option to enable CPU freq plugin but when I go to tic the plugin, that whole program crashes. Probably somthing I am doing wrong.

---

### Post by Werne on 2013-11-16
> **ventrical said:**
> I have noticed that when I have stressed a CPU to a max it will not act the same way at normal speeds - almost sort of buggy. 

  I do most of my own mods also. All of the above .. you're right. Good advice! Thanks.
Reason for misbehavior is die degradation. Long exposure to voltages out of the normal voltage range degrades the transistors in the die, resulting in a CPU that cannot operate at the same level of efficiency as it operated at on stock. Transistors basically can't work as well as they did. That's why I avoid using voltages outside the Turbo range on my CPU unless for short-term tests or benchmarking (as I said a few pages back, I'll be keeping it at 1.428V for everyday work).

And I always make my own mods, I find it fun, I get to use what I know (I didn't finish electromechanical engineering for nothing) and I save money. Awesome all around. :D

> **ventrical said:**
> btw .. with your VRMs running hot like that  then watch your caps (if  they still have them on those MoBos). I even make my own heat syncs but  that is intricate work. I had to shave and bore some fins on one of my  CoolerMaster sinks so they don't bump up against a row of caps (which  was not affected by the original heat sink for that machine.)
Nah, my VRMs don't have caps, it's some capless design thingy on these Revision 3 boards. And if VRMs get too hot, the CPU will throttle, it even has VRM protection which is nice. VRMs are running cool now, and I solved the throttling issue I had (dual-bios was making issues), so I'm ready to push into 1.456V range. I used to make my own heatsinks too but I figured out it all runs cool if I just replace the thermal compound, so now I put AC MX-4 under every heatsink as soon as I pull the components out of the box. Even my graphics card is running 12C cooler after thermal compound replacement. ;)

Unfortunately, further overclocking will have to wait till tomorrow, my wife is charging her cellphone on my USB port which will take a while, so rebooting is not an option at the moment. And here I thought ErP is a stupid option to keep on in BIOS... :roll:

---

### Post by ventrical on 2013-11-16
A break here too. I have 9 desktops and 3 laptops in my Ubuntu Shack with more than 20 installs of various flavors that need maintainence , plus  chores and it's Saturday! :)

Regards..

---

### Post by ventrical on 2013-11-21
Have had absolutely (zero) time to overclock. :(  Also rebuilding a heatsink on an AMD ... phewph!

---

### Post by Werne on 2013-11-21
I did have some time for overclocking, and a lot of trouble.

It would seem that my on-chip sensor is 14C off, meaning that my 48C maximum temperature is actually 62C die temp, at which the CPU started throttling. And I disabled the safety feature to stop the throttling, thinking it's gone bonkers, getting the CPU to 52C reported temperature after reaching 4.92GHz @1.480V, which is actually 66C die temp. Measured temps on my cooler base, 52C reported, 64C on cooler, added 2C to account for thermal conductivity loss. The chip's maximum temperature according to AMD is 62C, having 60C constant while running CPU-intensive tasks wouldn't be nice.

So it would seem I need a better CPU cooler, for now I went back to stock voltage and 4.2GHz until I can afford a better one. 5GHz was just one step away and I had to let it go. :(

But at least I came close. Lots of 8320s can't even come that close to 5GHz, plenty of them can't even go over 4.5GHz, some 8350s are also unable to reach 5GHz. And I could've got to it, at a voltage considered normal for 8350s hitting 5GHz. So along with being sad for not getting there, I'm also glad for even coming that far. :D

---

### Post by ventrical on 2013-11-21
> **Werne said:**
> I did have some time for overclocking, and a lot of trouble.

So it would seem I need a better CPU cooler, for now I went back to stock voltage and 4.2GHz until I can afford a better one. 5GHz was just one step away and I had to let it go. :(


Smart move.  I know you will get there  eventually.  When I pushed this little kitten of a Pentium 4 3.20GHz Cedar Mill to 5GHz I knew then that the kitten became a tiger. Then , 5.2GHz ... and on stock cooling with a little mod .. it was all worth the effort. I'm am not ready to go out and purchase liquid nitrogen atm .. what fun would that be anyways :)lol

Getting past 5GHz gave me a sense of accomplishment. I still plan to keep on tweaking. :)

Regards

---

### Post by ventrical on 2013-11-21
No luck here with my AMD AthlonX2-6000 I can get it up to 3.45GHz and thats it . Just a real pain  :)

---

### Post by Werne on 2013-11-26
> **ventrical said:**
> No luck here with my AMD AthlonX2-6000 I can get it up to 3.45GHz and thats it . Just a real pain  :)
Those never did overclock very high, single-core Athlons were pretty good though. Too bad my 939 mobo doesn't work (just spins the fans up and down every second), I have an Athlon 64 3200+ (90mn Venice) that was running at 3.12GHz (2GHz stock) without even touching VCore, only NB voltage, mobo didn't have CPU voltage adjustments which is just sad. I bet this thing could come up to some 5GHz easily, Venice could take up to 1.65V VCore while stock is 1.35V.

And while I did found a way to make this thing run on lower temperatures, I can't say I like it. A friend of mine wanted to throw away a 120cm 6200RPM fan used for special effects, so I saved it from going into a scrap heap. It'll definitely keep the CPU cool, without a doubt, even without a heatsink and system fans, if it doesn't blow the PC through a wall that is. Not to mention the noise this thing makes, it sounds like a MiG-21 taking off, and I worked on a military airport so I know how a MiG-21 sounds! :o

---

### Post by ventrical on 2013-11-28
> **Werne said:**
> Those never did overclock very high, single-core Athlons were pretty good though. Too bad my 939 mobo doesn't work (just spins the fans up and down every second), I have an Athlon 64 3200+ (90mn Venice) that was running at 3.12GHz (2GHz stock) without even touching VCore, only NB voltage, mobo didn't have CPU voltage adjustments which is just sad. I bet this thing could come up to some 5GHz easily, Venice could take up to 1.65V VCore while stock is 1.35V.

And while I did found a way to make this thing run on lower temperatures, I can't say I like it. A friend of mine wanted to throw away a 120cm 6200RPM fan used for special effects, so I saved it from going into a scrap heap. It'll definitely keep the CPU cool, without a doubt, even without a heatsink and system fans, if it doesn't blow the PC through a wall that is. Not to mention the noise this thing makes, it sounds like a MiG-21 taking off, and I worked on a military airport so I know how a MiG-21 sounds! :o


  Coincidently I just happened across a 939 board. I got a 3800 X2  and quite sure a 6400 3200+. No heat sync so I'll have to build one. Thanks for your info and experience. It will come in handy. :)

btw .. I don't mind loud fans as long as they keep my hardware cool :)

Edit:

That was an absolute fail. I think the CPU is gone. I'll try another... later.

---

### Post by Werne on 2013-11-28
> **ventrical said:**
> Coincidently I just happened across a 939 board. I got a 3800 X2  and quite sure a 6400 3200+. No heat sync so I'll have to build one. Thanks for your info and experience. It will come in handy. :)
Damn, and I can't find a single 939 board around. That sucks, the only one I can found that supports that Athlon 3200+ is an AM2 board which uses DDR2 RAM, and I'm all out of DDR2 right now, all I have is about 13GB of DDR-400.

By the way, you can fit any AMD heatsink onto a 939 board. AM2, AM2+, AM3, AM3+, FM1 and FM2 (even older like 754) can all be used on 939, they are all interchangeable since there's only a tiny bit of difference between them (for example, 939 board has a plastic frame around the CPU base while an AM3/AM3+ doesn't, and so on). I used a stock cooler from my FX 8320 when I tested the 939 board I have, it fit in there like a charm.

> **ventrical said:**
> btw .. I don't mind loud fans as long as they keep my hardware cool :smile:
Yeah, well, it's kinda hard to overclock when you can't even hear your own thoughts, and my wife doesn't like the noise much, so I found a good and quiet way to lower temps.

I got a Chieftec Aegis CH-05B-B case yesterday and I transferred my components into it. Now I have two 120mm fans blowing air over my CPU cooler (one blowing directly over it, one exhausting the heat), one 120mm fan on top of the case (exhausting hot air), and two 92mm fans on the front (pulling air in). I also downclocked the memory to reduce the amount of heat on the CPU memory controller. Dropped the temps from 44.8C under full load on stock voltage, down to 36.4C, 6 degrees improvement and the ambient temp got raised a few degrees since last time (fixed the heating system). And since I requested a new board due to a faulty sensor, I currently really do have 36.4C on the CPU die. Nice, maybe now I can reach 5GHz. :D


EDIT: Nope, anything over +0.050V results in a sharp rise in temperatures, I can reach 4.4GHz on 1.356V with 41.4C tops, but once I go 4.5GHz on 1.380V I have a maximum temperature of 48.6C, 4.6GHz on 1.404V is 55.1C max and 4.72GHz on 1.428V is 61.2C max. Seems I've milked everything bit of cooling performance I can out of this cooler, now there's only one thing left - buy a new one. Been thinking about Antec H2O 920 water cooling but that'll wait a bit, ain't got money for that. I'd build my own water loop if the CPU plate and radiator were cheaper, I already have all the other parts like the tank, pump, tubing, etc.

---

### Post by ventrical on 2013-11-30
Thanks for the update Werne. 

  I  have been so busy .... even locked my keys in my car the other day all while picking up a DQ35JOE MoBO for a Intel Core2Duo 3.GHz processor. What a corrnundrum!!. :)

 Sounds intriguing what you are doing with your O'Clocking.!

I'll be back at this ..

---

### Post by ventrical on 2014-01-11
I switched over to Lubuntu @5.127GHz running nvidia-current and it seems to be more stable than nouveau.

This, of course, running the..

```



ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-2-generic #17-Ubuntu SMP Fri Jan 10 12:14:58 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 

```

  Just to test stability I am going to install ubuntu-desktop  (unity) at this high rate of speed.

---

### Post by ventrical on 2014-01-11
> **ventrical said:**
> I switched over to Lubuntu @5.127GHz running nvidia-current and it seems to be more stable than nouveau.

This, of course, running the..

```



ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-2-generic #17-Ubuntu SMP Fri Jan 10 12:14:58 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 

```

  Just to test stability I am going to install ubuntu-desktop  (unity) at this high rate of speed.

Edit

Ok .. that done .. I only had to
```

 sudo dpkg --configure -a

```
once and it was a good Unity fix so I have Unity stable running on the 3.13.2.x.x kernel with nvidia-current.

Note:

 Installing nvidia current allowed me to work with PCIe frequencies without having major kernel panics. With nouveau these settings were very hard to maintain.

---

### Post by ventrical on 2014-02-04
Ok.. I installed this brand-new (older card Circa 2006) into my overclock box GeForce 7300GS PCI-E (which I think is outdated) and Unity 3D works just fine with the nVidia Driver and Settings etc.. I just have to build a fan for it. haven't tried to up the clock as of yet with this new card.

---

### Post by ventrical on 2014-02-04
All is running cool here.

```

ventrical@ventrical-Asus-Overclock:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.62 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.59 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed: 2518 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +38.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +16.0°C  (high = +80.0°C, crit = +125.0°C)

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5126 MHz
ventrical@ventrical-Asus-Overclock:~$ 


```

Odd thing. I don't have to click on any icons in the Unity Greeter to log in.  hmmmmm..

Time to install razorqt ... at full speed (5.126GHz)

---

### Post by SurfaceUnits on 2014-02-05
How many Bogomips do you get at that speed? The Sysinfo utility will show you.

---

### Post by ventrical on 2014-02-05
> **SurfaceUnits said:**
> How many Bogomips do you get at that speed? The Sysinfo utility will show you.

I had some problems with razorqt and Lubuntu desktop. They both render a higher CPU temp than Unity 3D. I am in Unity 3D, trusty ( Linux ventrical-Asus-Overclock 3.13.0-3-generic #18-Ubuntu SMP Mon Jan 13 19:16:46 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ ) will update.

Current bogo mips:

---

### Post by ventrical on 2014-02-05
..and that bogomips reading is consistent with this method also:

```


ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-3-generic #18-Ubuntu SMP Mon Jan 13 19:16:46 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 5
cpu MHz        : 5127.232
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm
bogomips    : 10254.46
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 5
cpu MHz        : 5127.232
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm
bogomips    : 10254.46
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

ventrical@ventrical-Asus-Overclock:~$ 

```

---

### Post by ventrical on 2014-02-05
I was able to increase the speed after I set PCI-E to auto and increased frquency. Also had to raise vCore . I aiming for 5.2 GHz. Here goes.

edit: Not tonight :) I'll have to try a different hdd.

---

### Post by ventrical on 2014-02-06
The particular PC that I am using runs GRuB Rescue Disk (which uses LDXE and has an earlier kernel) from the CD at above 5.2xxGHz no problem. I tried some earlier Ubuntu distros and tried to run Trusty from USB (Lubuntu/Alpha) but as soon as I reach the 5.2GHz limit, Ubuntu chokes up with a kernel panic/not tainted/ can't find fs 0,0 block/sector etc.. so there must be a kernel problem with the current candidates which is preventing the overclock above 5.2GHz. Earlier distros of Ubuntu just lock up from the Live CD but Fedora 14 booted live but would not report correct cpu freq.

  Good thing is  that Trusty does provide for  a much faster and stable overclock with most recent kernel updates.

Just updating the situation here.

Regards..

---

### Post by ventrical on 2014-02-10
I put in 2 more sticks of 1 GB DDR @ 800MHz and it has become more stable during the update/upgrade process. (Total 4GBs)

Currently running at :

```

ventrical@ventrical-Asus-Overclock:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.58 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.61 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     3994 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed: 2657 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +48.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +34.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +16.0°C  (high = +80.0°C, crit = +125.0°C)


```

```

ventrical@ventrical-Asus-Overclock:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 5
cpu MHz        : 5159.842
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm
bogomips    : 10319.68
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 5
cpu MHz        : 5159.842
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm
bogomips    : 10319.68
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

ventrical@ventrical-Asus-Overclock:~$ 

```

---

### Post by ventrical on 2014-02-27
In summary, Ubutnu Trusty kernels have worked well on the Cedar Mill lith of P4 3.2 GHz (single core) processor overclocked to 5.12GHz stable on air cooling only.. My choice of fan was from an old HP tower with Cooler Master Fan. The processor never really overheated as  the system would mostly kernel panic above 5.2GHz. I'll keep trying different processors as I aquire them.

 For now .. I am on to experimenting with the Intel Core 2 Quad 2.4GHz(Q6600) on the ASUS P5QL Pro. I am currently overclocked to 3.259GHz with no problems using Trusty current amd64 install.
  Regards..

---

### Post by ventrical on 2014-03-27
I disabled SS  in BIOS on CPU and PCIE and now I have this:

```


ventrical@ventrical-P5QL-PRO:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 3800 MHz
    Current Speed: 4991 MHz

```

but 

```

cat /proc/cpuinfo 

```

gives me this:

```

ventrical@ventrical-P5QL-PRO:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1603.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6300.16
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1603.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6300.16
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1603.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6300.16
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1603.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6300.16
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


```

which is consistent with the bogomips reported by sysinfo from software center.

---

### Post by ventrical on 2014-04-08
On my Cedar Mill 3.20GHz P4 I am still rolling with the new 3.13.0-23 trusty kernel :)

```

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 5127 MHz
ventrical@ventrical-Asus-Overclock:~$ 

```

```

ventrical@ventrical-Asus-Overclock:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.54 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.60 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.61 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.14 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4090 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed: 2721 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +45.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +34.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +10.0°C  (high = +80.0°C, crit = +125.0°C)

ventrical@ventrical-Asus-Overclock:~$ 

```

---

### Post by Werne on 2014-04-15
An email from Canonical reminded me I haven't been around here for a while, been hanging out on OCN as of lately, drooling over some of the PCs over there. Changed the cooler and RAM in the meantime too, currently rocking Scythe Mugen 4 PCGH with two 120mm 1000RPM Scythe GlideStream fans and one stick of 8GB DDR3-1600 10-10-10-30 G.Skill RipjawsX I clocked up to 2144MHz 10-12-11-34. And that single-channel stick is faster than my old 1866 CL13 RAM in dual-channel (yes, my old RAM was that pathetic).

Current 24/7 overclock is 30% and running cool.
```
werne@ubuntu-devel:~$ cat /proc/cpuinfo|grep "cpu MHz"
cpu MHz        : 4556.173
cpu MHz        : 4556.173
cpu MHz        : 4556.173
cpu MHz        : 4556.173
cpu MHz        : 4556.173
cpu MHz        : 4556.173
cpu MHz        : 4556.173
cpu MHz        : 4556.173

```
All 8 cores enabled, upped BCLK to 268MHz and dropped CPU multiplier to 17 which allowed for 4.556GHz at 1.368V on the CPU and 2144MHz at 1.650V on RAM. For some reason I can hit lower latencies on the RAM if I keep the multi lower and up base clock instead, CL10 on x8 multi and 268MHz BCLK as opposed to CL12 on x10.66 multi and 200MHz BCLK, had to push my Northbride to 1.140V in order to get there though but up to 1.175V is safe. CPU is kept at around 50C which is also good since max temp according to AMD is 62C, and that's with quiet 1000RPM fans. No throttling either, I put a thermal controlled 2000RPM 92mm fan over the VRM heatsink to make sure of that.

All in all, things are looking good, I just need to cut a hole in my motherboard tray and put a fan to blow on the socket and back of VRMs, then I'll be pushing further. Sucks that I can't get any Noctua fans around here, those would do a great job keeping my CPU both cool and quiet, but GlideStreams do a good job as well.

---

### Post by ventrical on 2014-04-16
Thanks for the update werne. Those are some expensive fans :)lol I have to settle for what I can build and improvise from older throw-a-ways. I'm out to look for another power supply.

---

### Post by ventrical on 2014-04-16
> **Werne said:**
> Sucks that I can't get any Noctua fans around here, those would do a great job keeping my CPU both cool and quiet, but GlideStreams do a good job as well.

On my ASUS P5AD2-E Deluxe it has fanless cooling sync on the underside of the MoBo (right where the processor is). I think it is a fridge-fet. It really helps in keeping the processor temps down. I do not see the fanless cooling technology on the newer boards. Perhaps they are for custom only.

---

### Post by Werne on 2014-04-17
> **ventrical said:**
> Those are some expensive fans :)lol I have to settle for what I can build and improvise from older throw-a-ways. I'm out to look for another power supply.
Hell, I got those for $5 off the used market, they ran for three days in the guy's PC since he bought the wrong fans. There's even a three months old Noctua NH-D14 there for $50 but I'd have to modify my case to fit it in so it's a no-go. Right now I'm eyeballing a fully-modular XFX 650 PSU some local guy is selling, I need a modular since I can't manage the cables at all in my case, for now I just pulled them into the 3.5" bay compartment and zip-tied them to stay put. :D

> **ventrical said:**
> On my ASUS P5AD2-E Deluxe it has fanless  cooling sync on the underside of the MoBo (right where the processor  is). I think it is a fridge-fet. It really helps in keeping the  processor temps down. I do not see the fanless cooling technology on the  newer boards. Perhaps they are for custom only.
I had that board but I don't recall it having a socket heatsink. Then again, I bought it used, maybe someone ripped it off.

Gotta  admit though, a socket heatsink would be handy for a Piledriver, socket on these  things gets hot as hell.

---

### Post by ventrical on 2014-04-18
It's called this:

---

### Post by ventrical on 2014-04-26
Back at it here. I was able to just now get easily and safely to  5.207 GHz with Utopic Unicorn running the Lubuntu Netbook desktop.  It is just awesome.. and it is running as cool as a cucumber.. All I had to do was up the PCI Chipset voltage. I had to crank it in the red zone then bring up the CPU to 1.625v.

 I also put one hard 2GB DDR2 stick in there. (single channel).800MHz

 I'm going to take it up and see how high I can get this but, 55C CPU temp is my limit for now.

```

ventrical@ventrical-Asus-Overclock:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.59 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.60 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.14 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4017 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed: 2616 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +41.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +30.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:   +9.0°C  (high = +80.0°C, crit = +125.0°C)

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5207 MHz
ventrical@ventrical-Asus-Overclock:~$ 



```

---

### Post by ventrical on 2014-04-26
sysinfo results

---

### Post by ventrical on 2014-09-02
Back at it here with:

```

Linux ventrical-Satellite-A105 3.16.0-12-generic #18-Ubuntu SMP Mon Sep 1 13:06:35 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

I put in a new nVidia card and upgraded to full ubuntu-unity install.(Utopic). I did this at 5.047GHz for starters. Also have an SSD hdd in there (ver3 with rollback) so that may help. (or it may not) :)

---

### Post by ventrical on 2014-09-05
The SSD did no good for syncing issues and kernel panic.. I am now back at 5.120GHz, cool as a cucumber. I'm going to keep working at this.

Also .. after updates today .. can't run Extreme Tux Racer . Used to be able to on this little -

```


04:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 GS] (rev a1)

```


so i am going to try an stick a Quattro in there. :) lol


```

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5127 MHz
ventrical@ventrical-Asus-Overclock:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.61 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.54 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.04 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4041 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +38.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +10.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +38.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +130.0°C, hyst =  +2.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-Asus-Overclock:~$ 

```

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.16.0-13-generic #19-Ubuntu SMP Thu Sep 4 23:02:21 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 

```

---

### Post by ventrical on 2014-09-06
Before I [I]put a new adapter card in I am trying this : to syncronize the PCI clock to CPU  rather than Auto and I am now running at this speed with stable.

```

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5207 MHz
ventrical@ventrical-Asus-Overclock:~$ sensors

```

Edit: This was a fail.  I juiced it to 1.7 volts and it crashed. Had to manually reset CMOS. I have been getting reports about Alsa audio driver which I think is onboard audio and so I'll disable that and see if it helps any.
[/I]

---

### Post by ventrical on 2015-04-08
Just an update.

 I am running hard install of vivid-ubuntu-unity from daily. amd64bit. I have installed:

```

04:00.0 VGA compatible controller: NVIDIA Corporation G71GL [Quadro FX 3500] (rev a1)
ventrical@ventrical-System-Product-Name:~$ 

```

and it is running unity very fast with very fast boot on a rather slow drive.  I am having a problem , though, getting stable past 5.00GHz so I will try the razorqt desktop and experiement .. plus add some voltage ..etc.

On bootup vivid is giving me an error about reaching thermal limits (which it did not do with previous versions) and it is an /f/p but this is older board with Pentium (R) 3.20 HT Cedar Mill single core but the nVidia card has made all the difference. Got that from yard sale for next to nothing.

Regards..

```

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 4903 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2015-05-06
I switched processor to a Celeron D 3.20GHz SL9KM/533FSB and I have a stable overclock on air @ 5.O51GHz running unity desktop via GDM at amd64bit!

It is very smooth, no jumpy video and very responsive. I can update/upgrade with stability.

```


ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.57 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.59 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.61 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +31.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:   +5.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +50.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +2.0°C)
                       (emerg = +110.0°C, hyst = +10.0°C)

ventrical@ventrical-System-Product-Name:~$ uname -a
Linux ventrical-System-Product-Name 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5AD2-E-Deluxe v: Rev 1.xx
           Bios: American Megatrends v: 1005.002 date: 01/19/2006
CPU:       Single core Intel Celeron D (-UP-) speed: 5051 MHz (max)
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 160.0GB (4.5% used)
Info:      Processes: 170 Uptime: 21 min Memory: 622.4/2000.6MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-System-Product-Name:~$ 

```

Regards..

---

### Post by ventrical on 2015-05-09
I built my 'howler' for my Wolfdale Processor to test wily werewolf.  Lots of work. Now I have to take out the old fan (Intel Snoozer- zzzzzzz +) and put in the modified howler. :)lol

Regards..

---

