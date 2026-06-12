---
title: "Spike in ram usage after sleep mode"
date: 2021-12-05
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2021-12-05
Screenshot: [https://i.imgur.com/dx732im.png](https://i.imgur.com/dx732im.png)

Before:
```
[FONT=monospace][COLOR=#000000]MiB Mem :[/COLOR][COLOR=#000000]**  16009.6 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**  12734.5 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**   1656.5 **[/COLOR][COLOR=#000000]used,[/COLOR][COLOR=#000000]**   1618.6 **[/COLOR][COLOR=#000000]buff/cache [/COLOR]
MiB Swap:[COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**      0.0 **[/COLOR][COLOR=#000000]used.[/COLOR][COLOR=#000000]**  14024.4 **[/COLOR][COLOR=#000000]avail Mem[/COLOR]
[/FONT]
```
After:
```
[FONT=monospace][COLOR=#000000]MiB Mem :[/COLOR][COLOR=#000000]**  16009.6 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**  12128.5 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**   2255.7 **[/COLOR][COLOR=#000000]used,[/COLOR][COLOR=#000000]**   1625.3 **[/COLOR][COLOR=#000000]buff/cache [/COLOR]
MiB Swap:[COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**      0.0 **[/COLOR][COLOR=#000000]used.[/COLOR][COLOR=#000000]**  13424.1 **[/COLOR][COLOR=#000000]avail Mem[/COLOR]
[/FONT]
```

Noticed this earlier when i woke the system as suddenly was using 6GB when i was using around 4GB

```
Operating System: Kubuntu 22.04
KDE Plasma Version: 5.23.4
KDE Frameworks Version: 5.88.0
Qt Version: 5.15.2
Kernel Version: 5.16.0-051600rc4-generic (64-bit)
Graphics Platform: X11
Processors: 12 × AMD Ryzen 5 3600 6-Core Processor
Memory: 15.6 GiB of RAM
Graphics Processor: Radeon RX 580 Series
```

---

### Post by pqwoerituytrueiwoq on 2021-12-07
Before:
```
[FONT=monospace][COLOR=#000000]Tasks[/COLOR][COLOR=#000000]** 360 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**   1 **[/COLOR][COLOR=#000000]running,[/COLOR][COLOR=#000000]** 357 **[/COLOR][COLOR=#000000]sleeping,[/COLOR][COLOR=#000000]**   0 **[/COLOR][COLOR=#000000]stopped,[/COLOR][COLOR=#000000]**   2 **[/COLOR][COLOR=#000000]zombie [/COLOR]
%Cpu(s):[COLOR=#000000]**  1.0 **[/COLOR][COLOR=#000000]us,[/COLOR][COLOR=#000000]**  0.5 **[/COLOR][COLOR=#000000]sy,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]ni,[/COLOR][COLOR=#000000]** 98.4 **[/COLOR][COLOR=#000000]id,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]wa,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]hi,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]si,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]st [/COLOR]
MiB Mem :[COLOR=#000000]**  16009.6 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**   8171.3 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**   3312.5 **[/COLOR][COLOR=#000000]used,[/COLOR][COLOR=#000000]**   4525.9 **[/COLOR][COLOR=#000000]buff/cache [/COLOR]
MiB Swap:[COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**      0.0 **[/COLOR][COLOR=#000000]used.[/COLOR][COLOR=#000000]**  12246.3 **[/COLOR][COLOR=#000000]avail Mem [/COLOR][/FONT]
```
After:
```
[FONT=monospace][COLOR=#000000]Tasks:[/COLOR][COLOR=#000000]** 531 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**   1 **[/COLOR][COLOR=#000000]running,[/COLOR][COLOR=#000000]** 528 **[/COLOR][COLOR=#000000]sleeping,[/COLOR][COLOR=#000000]**   0 **[/COLOR][COLOR=#000000]stopped,[/COLOR][COLOR=#000000]**   2 **[/COLOR][COLOR=#000000]zombie [/COLOR]
%Cpu(s):[COLOR=#000000]**  1.0 **[/COLOR][COLOR=#000000]us,[/COLOR][COLOR=#000000]**  0.5 **[/COLOR][COLOR=#000000]sy,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]ni,[/COLOR][COLOR=#000000]** 97.9 **[/COLOR][COLOR=#000000]id,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]wa,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]hi,[/COLOR][COLOR=#000000]**  0.5 **[/COLOR][COLOR=#000000]si,[/COLOR][COLOR=#000000]**  0.0 **[/COLOR][COLOR=#000000]st [/COLOR]
MiB Mem :[COLOR=#000000]**  16009.6 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**   6784.8 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**   4670.6 **[/COLOR][COLOR=#000000]used,[/COLOR][COLOR=#000000]**   4554.2 **[/COLOR][COLOR=#000000]buff/cache [/COLOR]
MiB Swap:[COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]total,[/COLOR][COLOR=#000000]**  16384.0 **[/COLOR][COLOR=#000000]free,[/COLOR][COLOR=#000000]**      0.0 **[/COLOR][COLOR=#000000]used.[/COLOR][COLOR=#000000]**  10888.5 **[/COLOR][COLOR=#000000]avail Mem[/COLOR][/FONT]
```
After sleep ram usage is up by 1.2GB
Screenshot: [https://i.imgur.com/MpmSTKm.png](https://i.imgur.com/MpmSTKm.png)

---

