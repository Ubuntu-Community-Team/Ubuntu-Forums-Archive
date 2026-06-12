---
title: "CPU usage not balanced over all cores"
date: 2012-09-17
forum: Server Platforms
---

### Post by spark3y on 2012-09-17
Hi,

Please tell me if the below is normal? I am running apache2 on a webserver but i cant get ubuntu to sort the load on the different cpu cores. As stated below it preferes to but everything on cpu0 but i would rather have it balanced over all the cores.

I am running Ubuntu 12.04 on ESXi 5.0.

```

Linux 3.2.0-23-generic (Server)  2012-09-17      _x86_64_        (12 CPU)

19:34:00     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
19:34:00     all    0,62    0,00    0,21    0,00    0,00    0,08    0,00    0,00   99,09
19:34:00       0    6,05    0,00    0,87    0,00    0,00    0,99    0,00    0,00   92,08
19:34:00       1    0,37    0,00    0,23    0,00    0,00    0,00    0,00    0,00   99,39
19:34:00       2    0,14    0,00    0,07    0,00    0,00    0,00    0,00    0,00   99,79
19:34:00       3    0,05    0,00    0,01    0,00    0,00    0,00    0,00    0,00   99,94
19:34:00       4    0,03    0,00    0,01    0,00    0,00    0,00    0,00    0,00   99,96
19:34:00       5    0,02    0,00    0,01    0,00    0,00    0,00    0,00    0,00   99,97
19:34:00       6    0,02    0,00    0,02    0,00    0,00    0,00    0,00    0,00   99,96
19:34:00       7    0,57    0,04    1,02    0,01    0,00    0,00    0,00    0,00   98,35
19:34:00       8    0,03    0,00    0,06    0,00    0,00    0,00    0,00    0,00   99,91
19:34:00       9    0,06    0,00    0,11    0,00    0,00    0,00    0,00    0,00   99,82
19:34:00      10    0,01    0,00    0,01    0,00    0,00    0,00    0,00    0,00   99,98
19:34:00      11    0,05    0,00    0,09    0,00    0,00    0,00    0,00    0,00   99,86

```

Here is also a printscreen of the htop command.
[http://tinypic.com/r/35jh1g7/6]("http://tinypic.com/r/35jh1g7/6")

Best regards

---

### Post by youngunix on 2012-09-17
That is normal as far as I can tell. Take a look at this [thread]("http://www.tomshardware.com/forum/273054-28-core-work-load").

---

