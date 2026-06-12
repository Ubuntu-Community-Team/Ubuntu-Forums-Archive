---
title: "Ralink Wireless not working in realtime kernel, but working in generic!"
date: 2010-10-31
forum: Ubuntu Studio
---

### Post by marcoharder on 2010-10-31
Hi!


I set up another Ubuntu Studio recording PC and put in an old Ralink USB wireless interface. While it was working using the generic kernel [using blacklist rt2800usb in /etc/modprobe.d/blacklist.conf] I couldn't seem to get it to work while booted in the realtime kernel. How do I get it to work?

Thanks in advance!

MH

---

### Post by marcoharder on 2010-11-07
Help, anyone?

---

### Post by trulan on 2010-11-08
Which realtime kernel are you using?  If you have the one from abogani's ppa or falkTX's ppa, you could try the one from bojo42's ppa:
[https://launchpad.net/~bojo42/+archive/rt](https://launchpad.net/~bojo42/+archive/rt)
from what I understand, this kernel is configured more closely to the generic kernel (more modules enabled) and that might be of some help here.

Or, if you could figure out which module/modules are being used for wireless on the generic kernel
```
lsmod
```
then we could see if those modules are present in the realtime kernel, and what it might take to get them there and loaded.

---

### Post by marcoharder on 2010-11-11
And it works! Bristol gets more xruns on rt than on realtime, but it's more bearable than generic! Thanks trulan!

---

