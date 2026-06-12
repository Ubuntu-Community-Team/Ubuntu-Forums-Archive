---
title: "Command line problems testing printing in 9.04"
date: 2009-06-01
forum: Server Platforms
---

### Post by normanp on 2009-06-01
With Server 7.10 I did the following successfully having plugged in a USB LaserJet 1010:
lpinfo -v       List includes 'Direct usb://HP/Laserjet ' etc
lpoptions -d LaserJet
lpstat -s       Confirms default destination and device
lp test.txt     Prints after a long delay, but at least confirms that it is possible.

With Server 9.04 lpinfo -v gives the same result as above, but lpoptions -d LaserJet gives me: 'Unknown printer or class' and lpstat -s gives 'no system default' and 'no destinations added'.

What have I done wrong?
Thanks

---

