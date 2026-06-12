---
title: "Can I virtualize 64bit?"
date: 2008-04-18
forum: Virtualisation
---

### Post by StOoZ on 2008-04-18
I using an old CPU, Athlon XP barton 2500+ which is 32bit (x32).
now I wonder, is it possible to install somewhow windows server 2008 x64 on VMware ?

---

### Post by DarkFox.DK on 2008-04-20
> **StOoZ said:**
> I using an old CPU, Athlon XP barton 2500+ which is 32bit (x32).
now I wonder, is it possible to install somewhow windows server 2008 x64 on VMware ?

No, unless you have a 64-bit cpu you can't.

From VMwares KB: While it is theoretically possible to emulate a 64-bit instruction set on 32-bit hardware, doing so most likely results in unacceptable performance degradation.
[http://kb.vmware.com/selfservice/viewContent.do?language=en_US&externalId=1901](http://kb.vmware.com/selfservice/viewContent.do?language=en_US&externalId=1901)

---

### Post by FredB on 2008-04-21
> **StOoZ said:**
> I using an old CPU, Athlon XP barton 2500+ which is 32bit (x32).
now I wonder, is it possible to install somewhow windows server 2008 x64 on VMware ?

You cannot.

Only 64bits CPUs (nearly all of them since end of 2006 or so) can virtualize both 32 and 64 bits OS.

---

### Post by -Rick- on 2008-04-22
Actually, you can with Qemu but it's very slow...

---

