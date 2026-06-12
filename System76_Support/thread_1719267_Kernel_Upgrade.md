---
title: "Kernel Upgrade"
date: 2011-04-01
forum: System76 Support
---

### Post by BuggyFunBunny on 2011-04-01
I've got some SSD on 10.04 Ratel.  Turns out 2.6.38 is the good kernel for SSD.  

I came across this page:
[http://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2638onubuntu1004lucidfromubuntu1104nattytheeasyway](http://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2638onubuntu1004lucidfromubuntu1104nattytheeasyway)

which claims that the upgrade is harmless and painless (my interpretation).  Is this true?

---

### Post by isantop on 2011-04-01
Actually, TRIM is enabled in the 2.6.35 kernel too, which is the default for Maverick. I'd recommend that instead, as it's much less likely to botch your system than using a different kernel version.

---

### Post by ajgreeny on 2011-04-01
Just as a warning, I tried the 2.6.36, 2.6.37 and 2.6.38 kernels from the lucid kernel ppa repository and found they all degraded usb read/write speed to the point that they were unusable, a few KB/sec.  I now use the 2.6.35-28 kernel from the "proposed updates" of software sources, and that slow usb problem has gone away.

It was taking about an hour to make a ubuntu live usb startup disk with the ppa kernels, but is now back to around 5 minutes.

---

