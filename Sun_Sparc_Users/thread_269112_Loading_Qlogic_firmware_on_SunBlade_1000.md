---
title: "Loading Qlogic firmware on SunBlade 1000"
date: 2006-10-01
forum: Sun Sparc Users
---

### Post by calixtine on 2006-10-01
Hi All,

I've installed Ubuntu dapper drake on a SunBlade1000 and it all works very well except the fans are on full-blast all the time. To fix this I've compiled a 2.6.18 kernel with the bbc_i2c driver that controls the fan speed. The Ubuntu supplied kernel has a cpu-hogging problem if you load the driver, however this was fixed in 2.6.17 (thank you, Mr Miller!)

My problem is I can't work out how to get the firmware blob for the qlogic host bus adapter loaded on boot with my freshly compiled kernel, I get an error along the lines of :

qla2xxx Firmware image unavailable

I have downloaded the suggested firmware, put it in /lib/firmware and /lib/firmware/2.6.18/ but still get the error. Somehow the Ubuntu supplied kernel gets around the firmware loading issue, does anyone know how?

regards
Andy

-- 
Linux version 2.6.15-26-sparc64 (buildd@vivies) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Fri Sep 8 19:56:21 UTC 2006

---

### Post by elicriffield on 2006-10-23
I think you can compile the kernel with the old style "firmware in a kernel module" modules if you select that insted of the new modules. Its an option somewhere in make menuconfig

Eli

---

