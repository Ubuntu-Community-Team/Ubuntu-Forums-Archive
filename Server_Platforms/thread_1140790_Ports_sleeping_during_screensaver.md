---
title: "Ports sleeping during screensaver"
date: 2009-04-27
forum: Server Platforms
---

### Post by txr13 on 2009-04-27
We have a script running that continuously outputs data via the system serial port. Normally, this works just fine. However, when the screen blanks from disuse, the serial port stops responding until input reawakens the screen (and presumably, other system functions).

If this is the case--that the screensaver also causes other system components to sleep automatically--how can this behavior be disabled? We'd prefer the screensaver to stay enabled, but without sleeping other ports on the system.

Running Ubuntu Server 8.10 (Intrepid) with all updates applied.

---

