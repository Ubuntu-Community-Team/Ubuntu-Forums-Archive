---
title: "Post your battery info!"
date: 2009-11-26
forum: The Cafe
---

### Post by gletob on 2009-11-26
User's of laptop's and presumably UPS's post your batery info here!

Btw if you don't have Gnome Power manger or another application to pull up battery info you can punch in 
```
cat /proc/acpi/battery/BAT1/info
```in to the command line

Well here's mine, apparently I knocked the DC adapter plug out of my laptop and didn't notice it until the battery light on the front started to blink red.

```
Product: Laptop battery
Status: Charging
Percentage charge: 7.9%
Vendor: SANYO
Technology: Lithium Ion
Serial number: 
Model: MAL32b
Charge time: 1 hour 11 minutes
Capacity: 62.1% (Poor)
Current charge: 2.6 Wh
Last full charge: 33.1 Wh
Design charge: 53.3 Wh
Charge rate: 25.8 W
```or from the command line
```
glenn@glenn-laptop:~$ cat /proc/acpi/battery/BAT1/info 
present:                 yes
design capacity:         4800 mAh
last full capacity:      2983 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 480 mAh
design capacity low:     144 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            MAL32b
serial number:            
battery type:            LION
OEM info:                SANYO

```

---

### Post by Grifulkin on 2009-11-26
```
present:                 yes

design capacity:         2200 mAh

last full capacity:      1068 mAh

battery technology:      rechargeable

design voltage:          10800 mV

design capacity warning: 300 mAh

design capacity low:     42 mAh

capacity granularity 1:  32 mAh

capacity granularity 2:  32 mAh

model number:            UM08A31

serial number:           6069

battery type:            LION

OEM info:                SANYO

```

---

### Post by SomeGuyDude on 2009-11-26
```
present:                 yes
design capacity:         6000 mAh
last full capacity:      3424 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 177 mAh
design capacity low:     107 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard
```

Yikes. My capacity's pretty poor.

---

### Post by Exodist on 2009-11-26
```
present:                 yes
design capacity:         576000 mAh
last full capacity:      423424 mAh
battery technology:      renewable
design voltage:          14800 mV
design capacity warning: 177 mAh
design capacity low:     107 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            FUSION
OEM info:                Stark Weapon Systems
```

How is mine?

---

### Post by gletob on 2009-11-27
> **Exodist said:**
> ```
present:                 yes
design capacity:         576000 mAh
last full capacity:      423424 mAh
battery technology:      renewable
design voltage:          14800 mV
design capacity warning: 177 mAh
design capacity low:     107 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            FUSION
OEM info:                Stark Weapon Systems
```How is mine?


Hellatiously powerful.  Lol.

---

### Post by isbiyanto on 2010-05-18
isbiyanto@isbiyanto-laptop:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      1503 mAh
present voltage:         11002 mV
isbiyanto@isbiyanto-laptop:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         5183 mAh
last full capacity:      5183 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PABAS024
serial number:           3658Q
battery type:            LION
OEM info:                PANASONIC 

My battery can't charge. i must use my ac adapter to run my laptop :(

---

### Post by KristinaK on 2010-07-10
does it mean that ubuntu have battery problems?

---

### Post by Lucradia on 2010-07-10
it must be saturday.

/necro

---

