---
title: "&quot;SDB notify” problem from SiI3132 on Ubuntu 10.04 LTS"
date: 2011-12-01
forum: Ubuntu Dev Link Forum
---

### Post by buiducquynh on 2011-12-01
I’m developing a device driver for SiI3132 card, which is a PCI Express to SATA  controller on Ubuntu 10.04 LTS OS (kernel 2.6.32).My purpose is to use the card to control Port Multiplier.

Sometimes, SiI3132 card does not transfer the “SDB notify” interrupt.  Although via Bus Doctor, I saw the Port Multiplier sent the “Set Device Bits” FIS packet to the SiI3132 card but the card did not deliver the interrupt. One more thing, the problem is only occurred with “SDB notify” interrupt source, while other interrupt source worked normally (for example: complete command and error command). 

I also tried to port the driver to RedHad 5 - kernel 2.6.18, the problem is never occurred. Everything is okay on Redhat.

I love Ubuntu because it is open source OS but unfortunately the Ubuntu makes the error.

Any advises or work-around on the problem? 

Thank in advance.

---

### Post by i_hope_so on 2011-12-05
querybts  will show you debian bugs which might be related since ubuntu is based on debian

---

