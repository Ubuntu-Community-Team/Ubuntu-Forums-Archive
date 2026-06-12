---
title: "Ubuntu 13.04 with a fall back to 12.10"
date: 2013-06-02
forum: System76 Support
---

### Post by starfury65 on 2013-06-02
I have the following laptop,

Gazelle Professional (gaz-p6)
Graphics Nvidia GeForce GTX 560M Graphics with 1.5GB GDDR5 Video Memory
Hard Drive 500 GB 7200 RPM SATA II
Memory 8 GB Dual Channel DDR3 SDRAM at 1333MHz - 2 X 4GB
Processor 2nd Generation Intel Core i7-2630QM Processor ( 6MB L3 Cache, 2.00GHz )
Wireless 802.11 B+G+N Wireless LAN + Bluetooth Combo Module

The issue is just my tail of upgrading.  I did not have any problem going from Ubuntu 11.04 to 12.04.  So I tried installing the latest and greatest Ubuntu 13.04.  Full, clean install along with the system76 drivers.  Everything seemed ok at first, but after a few days, I could not shutdown or up start properly.  The shutdown would stop with no messages stating what was going on and i would have to hold the off button until the machine powered off.  Since this was not a clean shutdown, I would get a grub menu on power on.  Sometime during the start up it would just sit, and I would have to power off.  

So I thought the issue may have been with the video driver, but after doing a full, clean install again, I have not found a solution. For kicks I install Mint 15, yes I know its still Ubuntu 13.04.  Again, for kicks.  Left the default video as is, and for the first install of a program, installed Google Earth via the mint Software Manager.  Restarted and there were the shutdown and restart problems again.  So whether or not it was Google Earth or something else, I really didn't feel like fighting with it.  So I fell back to 12.10 and so far everything is running smooth.

---

### Post by isantop on 2013-06-03
There's a kernel issue with the current version of Ubuntu. If you have all of the updates installed, it should start up every time without issues. If it does hang on shutdown, then you can hold Alt+PrtSc (Next to F12) and while holding them type in:

REISUB 

to reboot or 

REISUO

to shut down.

---

