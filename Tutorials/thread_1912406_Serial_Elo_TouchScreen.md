---
title: "Serial Elo TouchScreen"
date: 2012-01-20
forum: Tutorials
---

### Post by J05HYYY on 2012-01-20
I spend most of today trying to get a serial Elo touchscreen working (using a usb converter).

Eventually I found out that if I use:
```
inputattach --elotouch /dev/ttyUSB0
```

My screen worked.

I created a script:
```
#!/bin/bash
inputattach --elotouch /dev/ttyUSB

```

Saved it to /etc/init.d, ran "chmod a+x" and then "update-rc.d mytouchscreen defaults" so i'd run at startup.

Configuration was easy using touchconf.

This is just to let people know, and is a reminder to myself.

Yay.:D

---

