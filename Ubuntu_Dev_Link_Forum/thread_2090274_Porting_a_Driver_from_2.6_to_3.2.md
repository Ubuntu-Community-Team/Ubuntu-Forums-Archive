---
title: "Porting a Driver from 2.6 to 3.2"
date: 2012-12-01
forum: Ubuntu Dev Link Forum
---

### Post by da_steve123 on 2012-12-01
Hi,

I am trying to get a USB/GPIB device (agilent 82357a) working with ubuntu 12.04.
I am fairly new to drivers but i have been reading "Linux Device Drivers 3rd Ed" ([http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)). It very specifically says that it is for the 2.6 kernel.
There is already a driver for the 2.6 kernel in the linux-gpib project, but as the technology is old now i dont think it has been worth anyones time to update it for 3.2
What i would like to know is what are the general differences between the 3.2 and 2.6 kernel in terms of drivers?
Has the interface changed? Any general advice to how i should approach it?
This is the first time i am attempting to write/modify a device driver so any suggestions would be appreciated 
Thanks,
Stephen

Edit:
[http://sourceforge.net/projects/linux-gpib/develop](http://sourceforge.net/projects/linux-gpib/develop)
well i feel foolish :p

---

