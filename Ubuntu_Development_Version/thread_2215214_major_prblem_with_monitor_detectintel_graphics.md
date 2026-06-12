---
title: "major prblem with monitor detect/intel graphics"
date: 2014-04-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-04-05
Just found out that there are certain monitors that will give an auto-adjust/no-preset error during and after booting the amd64/i386 trusty dailys. For example:

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

on a Benq FP93G will produce what appears to be an xorg or unity bug of some sort, however it will work excellently on a standard IBM France 15" LCD display adapter.

 The refernece bug is 1303053  so now I am wondering of it is a  f/p.

 That would mean (using this monitor) I would give the qa tester a pass, so, is the tracker able to discern between the monitors that are being used?

 I just thought that this was important because some testers may report a fail when, in fact, all they need do is try a different monitor on the older legacy intel graphics.

---

