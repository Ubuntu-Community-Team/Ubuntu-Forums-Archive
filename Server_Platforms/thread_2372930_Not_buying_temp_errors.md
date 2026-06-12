---
title: "Not buying temp errors"
date: 2017-09-30
forum: Server Platforms
---

### Post by DigiAngel on 2017-09-30
Meh...I see this a fair amount:
```
08:01:58 ubuntu kernel: [10858.536253] CPU0: Core temperature above threshold, cpu clock throttled (total events = 11)
08:01:58 ubuntu kernel: [10858.536331] CPU1: Core temperature above threshold, cpu clock throttled (total events = 11)
08:01:58 ubuntu kernel: [10858.536421] CPU2: Core temperature above threshold, cpu clock throttled (total events = 11)
08:01:58 ubuntu kernel: [10858.536791] mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 128: 000000008844000f
08:01:58 ubuntu kernel: [10858.536820] mce: [Hardware Error]: TSC 13c277fe8ba0 
08:01:58 ubuntu kernel: [10858.536824] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 0 microcode 82d
08:01:58 ubuntu kernel: [10858.536828] mce: [Hardware Error]: CPU 1: Machine Check: 0 Bank 128: 000000008844000f
08:01:58 ubuntu kernel: [10858.536831] mce: [Hardware Error]: TSC 13c27800de00 
08:01:58 ubuntu kernel: [10858.536834] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 2 microcode 82d
08:01:58 ubuntu kernel: [10858.536838] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 128: 000000008845000f
08:01:58 ubuntu kernel: [10858.536840] mce: [Hardware Error]: TSC 13c27803b298 
08:01:58 ubuntu kernel: [10858.536868] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 4 microcode 82d
08:01:58 ubuntu kernel: [10858.537040] CPU3: Core temperature above threshold, cpu clock throttled (total events = 11)
08:01:58 ubuntu kernel: [10858.537239] mce: [Hardware Error]: CPU 3: Machine Check: 0 Bank 128: 000000008845000f
08:01:58 ubuntu kernel: [10858.537245] mce: [Hardware Error]: TSC 13c278167f88 
08:01:58 ubuntu kernel: [10858.537250] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 6 microcode 82d
08:01:58 ubuntu kernel: [10858.551955] CPU0: Core temperature/speed normal
08:01:58 ubuntu kernel: [10858.551958] CPU1: Core temperature/speed normal
08:01:58 ubuntu kernel: [10858.552004] mce: [Hardware Error]: CPU 1: Machine Check: 0 Bank 128: 000000008844000a
08:01:58 ubuntu kernel: [10858.552009] mce: [Hardware Error]: TSC 13c279dd7ce0 
08:01:58 ubuntu kernel: [10858.552014] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 2 microcode 82d
08:01:58 ubuntu kernel: [10858.552018] mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 128: 000000008844000a
08:01:58 ubuntu kernel: [10858.552020] mce: [Hardware Error]: TSC 13c279dd8478 
08:01:58 ubuntu kernel: [10858.552048] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 0 microcode 82d
08:01:58 ubuntu kernel: [10858.552079] CPU2: Core temperature/speed normal
08:01:58 ubuntu kernel: [10858.552255] CPU3: Core temperature/speed normal
08:01:58 ubuntu kernel: [10858.552545] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 128: 000000008845000a
08:01:58 ubuntu kernel: [10858.552554] mce: [Hardware Error]: TSC 13c279e13c98 
08:01:58 ubuntu kernel: [10858.552558] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 4 microcode 82d
08:01:58 ubuntu kernel: [10858.552562] mce: [Hardware Error]: CPU 3: Machine Check: 0 Bank 128: 000000008845000a
08:01:58 ubuntu kernel: [10858.552564] mce: [Hardware Error]: TSC 13c279e691e0 
08:01:58 ubuntu kernel: [10858.552568] mce: [Hardware Error]: PROCESSOR 0:30678 TIME 1506780118 SOCKET 0 APIC 6 microcode 82d
```

However sensors shows different:
```
it8721-isa-0a30
Adapter: ISA adapter
in0:          +3.06 V  (min =  +0.52 V, max =  +2.83 V)  ALARM
in1:          +2.87 V  (min =  +2.02 V, max =  +2.00 V)  ALARM
in2:          +2.22 V  (min =  +0.86 V, max =  +1.74 V)  ALARM
+3.3V:        +3.24 V  (min =  +2.76 V, max =  +3.86 V)
in4:          +0.86 V  (min =  +0.98 V, max =  +0.77 V)  ALARM
in5:          +0.84 V  (min =  +1.42 V, max =  +0.29 V)  ALARM
in6:          +1.37 V  (min =  +1.56 V, max =  +0.17 V)  ALARM
3VSB:         +3.22 V  (min =  +5.11 V, max =  +0.17 V)  ALARM
Vbat:         +3.31 V  
fan1:           0 RPM  (min =   79 RPM)  ALARM
fan2:           0 RPM  (min =   95 RPM)  ALARM
fan3:           0 RPM  (min =   15 RPM)  ALARM
temp1:        -94.0°F  (low  = +21.2°F, high = +179.6°F)  sensor = thermal diode
temp2:       +104.0°F  (low  = +69.8°F, high = -167.8°F)  sensor = thermal diode
temp3:       -198.4°F  (low  = +87.8°F, high = +77.0°F)  sensor = disabled
intrusion0:  ALARM

acpitz-virtual-0
Adapter: Virtual device
temp1:        +80.2°F  (crit = +194.0°F)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +98.6°F  (high = +221.0°F, crit = +221.0°F)
Core 1:       +98.6°F  (high = +221.0°F, crit = +221.0°F)
Core 2:       +96.8°F  (high = +221.0°F, crit = +221.0°F)
Core 3:       +96.8°F  (high = +221.0°F, crit = +221.0°F)

```

I've been monitoring and I don't see any change in temp, nor does the box even feel warm.  Is there a way to tell the kernel the real threshold?  Either that or my something else is borked..thank you

---

### Post by TheFu on 2017-09-30
The CPU temps are real.  Fix your cooling.

---

