---
title: "Misreported Memory"
date: 2010-10-12
forum: Ubuntu Studio
---

### Post by Precipitous on 2010-10-12
Two quick questions:

#1 - I just installed UbuntuStudio Maverick fresh on a brand new hard drive. My system has 4GB of RAM, but it is only being reported as 3GB. When I boot the computer, if I run the Memtest, all 4GB get reported and the tests all run fine with no errors. Before replacing the hard drive, I had run each release from Intrepid to Lucid, and always saw 4GB as well. Does anybody have a clue as to what is going on?

#2 - If I boot into the latest generic kernel, I boot to a regular desktop. If I try to boot to the latest low latency kernel (installed from Synaptic), I boot to a command prompt. What causes that?

A big thank you in advance to any and all who happen to respond.

---

### Post by Precipitous on 2010-10-13
> **Precipitous said:**
> Two quick questions:

#1 - I just installed UbuntuStudio Maverick fresh on a brand new hard drive. My system has 4GB of RAM, but it is only being reported as 3GB. When I boot the computer, if I run the Memtest, all 4GB get reported and the tests all run fine with no errors. Before replacing the hard drive, I had run each release from Intrepid to Lucid, and always saw 4GB as well. Does anybody have a clue as to what is going on?

#2 - If I boot into the latest generic kernel, I boot to a regular desktop. If I try to boot to the latest low latency kernel (installed from Synaptic), I boot to a command prompt. What causes that?

A big thank you in advance to any and all who happen to respond.
#1 Was solved by installing and running the PAE kernel instead of the regular one.

#2 Wasn't solved, but at least I now know that it is being caused by the  driver for my Nvidia GeForce 7300 not being compatible with xorg  1.9.

---

