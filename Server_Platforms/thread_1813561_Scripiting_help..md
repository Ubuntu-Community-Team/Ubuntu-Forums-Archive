---
title: "Scripiting help."
date: 2011-07-27
forum: Server Platforms
---

### Post by NormaJean on 2011-07-27
hi

I'm looking at setting up a script that ssh's into our netapp (server01) and then reports an *environmental chassis status list-sensors*
being relatively new to programming I'm a little lost. I've gotten this far:
> 
#!/bin/bash
SERVER="server01"
USR="root"
OUT="out.txt"
ssh $USR@$SERVER > $OUT
Any help would be appreciated :)

---

### Post by NormaJean on 2011-07-28
Okay, slowly getting there..
> 
#!/bin/bash
SERVER="server01"
USR="root"
OUT="out.txt"
ssh $USR@$SERVER  environment status chassis list-sensors > $OUT
exit 0This puts all the sensors into my txt, however I only want anything that has a temperature. 
Mainly 'MB Front Zone' and 'MB Rear Zone' 
> Sensor Name              State          Current    Critical     Warning     Warning    Critical
                                        Reading       Low         Low         High       High
-------------------------------------------------------------------------------------------------
[LEFT] LCD board Temperature    normal            21 C         0 C        10 C        42 C        52 C
MB Front Zone Temperaturenormal            26 C         0 C        10 C        49 C        58 C
MB Rear Zone Temperature normal            29 C         0 C        10 C        50 C        59 C
PSU1 Present             normal           good
PSU1 AC IN               normal           good
PSU1 12V                 normal           good
PSU1 5V                  normal           good
PSU1 FAN1                normal          3726 RPM    1800 RPM    1850 RPM      --          --
PSU1 FAN2                normal          3459 RPM    1800 RPM    1850 RPM      --          --
PSU2 Present             normal           good
PSU2 AC IN               normal           good
PSU2 12V                 normal           good
PSU2 5V                  normal           good
PSU2 FAN1                normal          3734 RPM    1800 RPM    1850 RPM      --          --
PSU2 FAN2                normal          3308 RPM    1800 RPM    1850 RPM      --          --
CPU 3.3V Active          normal          3356 mV       --        3135 mV     3465 mV       --
CPU 3.3V Standby         normal          3356 mV       --        3135 mV     3465 mV       --
CPU 5V                   normal          5169 mV       --        4750 mV     5250 mV       --
CPU 12V                  normal         11875 mV       --       11400 mV    12600 mV       --
SYS_FAN_1 Fan1           normal          2366 RPM    1200 RPM    1250 RPM      --          --
SYS_FAN_1 Fan2           normal          2210 RPM    1200 RPM    1250 RPM      --          --
SYS_FAN_2 Fan1           normal          2343 RPM    1200 RPM    1250 RPM      --          --
SYS_FAN_2 Fan2           normal          2260 RPM    1200 RPM    1250 RPM      --          --
NVRAM6-temperature-3     normal            28 C         0 C        10 C        50 C        64 C
NVRAM6-battery-3         normal          4032 mV     3649 mV     3849 mV     4250 mV     4250 mV
[/LEFT]
 
Back to the drawing board

---

### Post by NormaJean on 2011-07-28
Nevermind, I am an idiot. 
[PHP]#!/bin/bash
SERVER="server01"
USR="root"
ssh $USR@$SERVER  environment status chassis list-sensors | grep "LCD board Temperature" | awk '{print $5}'
[/PHP]

---

### Post by Jive Turkey on 2011-07-28
> **NormaJean said:**
> Okay, slowly getting there..
This puts all the sensors into my txt, however I only want anything that has a temperature. 
Mainly 'MB Front Zone' and 'MB Rear Zone' 
Back to the drawing board

```
#!/bin/bash
 SERVER="server01"
 USR="root"
 OUT="out.txt"
 ssh $USR@$SERVER environment status chassis list-sensors [COLOR="Red"]| egrep -i temperature[/COLOR] > $OUT
 exit 0
```

maybe?

---

### Post by CaptainMark on 2011-07-28
i notice your using variables that cannot be changed, you may as well type root@server01...... theres nothing wrong with this just seems a little odd,

---

