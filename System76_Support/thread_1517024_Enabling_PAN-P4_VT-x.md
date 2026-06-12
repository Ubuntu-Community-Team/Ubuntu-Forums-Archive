---
title: "Enabling PAN-P4 VT-x"
date: 2010-06-24
forum: System76 Support
---

### Post by r4e on 2010-06-24
Hello,

I'm trying to enable VT-x support on a Pangolin Performance PAN-P4 with a Core 2 Duo P8600 processor. This processor is supposed to have VT-x support as shown by lscpu:

```

r4e@kubuntu:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               800.000
**Virtualization:        VT-x**
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K

```

Also, it's shown as having VT-x here: [http://ark.intel.com/Product.aspx?id=35568](http://ark.intel.com/Product.aspx?id=35568)

Despite this I don't see anything in the BIOS for enabling VT-x. VirtualBox reports that VT-x is not operational and needs to be enabled in the host BIOS. Is there a BIOS upgrade for the PAN-P4 that allows VT-x to be enabled? Has anyone successfully gotten VT-x to work on PAN-P4's?

According to this thread, VT-x is enabled on System76 laptops, but it doesn't seem to be unless it's a VirtualBox bug: 

[http://ubuntuforums.org/showthread.php?t=1150755](http://ubuntuforums.org/showthread.php?t=1150755)

Thanks for your help!

r4e

---

### Post by isantop on 2010-06-25
Please email us at support...at...system76...dot...com

---

### Post by r4e on 2010-06-28
It turns out that this was likely a VirtualBox bug, since the latest release, 3.2.6, shows that VT-x is enabled.

Thanks for your help.

---

