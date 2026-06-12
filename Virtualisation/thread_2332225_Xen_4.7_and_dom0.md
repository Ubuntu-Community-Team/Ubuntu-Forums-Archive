---
title: "Xen 4.7 and dom0"
date: 2016-07-29
forum: Virtualisation
---

### Post by cxly15 on 2016-07-29
I installed Xen 4.7 from source and the domain list when using xl list shows that a domain is running, but that its name is null. I am on version 15.10. How do I fix this?

---

### Post by Tadaen_Sylvermane on 2016-07-29
2 things. Installing from source is usually a last resort. Is there a reason you didn't use Xen from the repos? 
Other, you need to upgrade to 16.04. 15.10 died this month. No more support for it so you won't get much help with it on these forums. If you need something longer than 9 months support then stick with either 14.04 or 16.04, supported till april of 2019 and 2021 respectively.

---

### Post by cxly15 on 2016-07-29
I installed xen from source because the version from the repos does not support vga passthrough when using qemu unless I missed the package. I would like to use 16.04 but it appears that the fglrx driver from amd no longer works which is something I need.

---

### Post by MAFoElffen on 2016-07-31
> **cxly15 said:**
> I installed xen from source because the version from the repos does not support vga passthrough when using qemu unless I missed the package. I would like to use 16.04 but it appears that the fglrx driver from amd no longer works which is something I need.
On the Xen versions, Xen has supported GPU passthrough since version 4.0.0. The Xen version in Ubuntu's repo for 16.04 is Xen v4.6.

Yes, the fglrx graphics driver package, yes there are issues of not being able to use that anymore. It is an issue of AMD not supporting it anymore and it not working with the current version of XServer. Depending on what GPU you have, you still have options in 16.04. There is the opensource AMD or Radeon drivers,... And AMD Chrysalis and AMD's proprietary binary drivers.

---

### Post by minimike2 on 2017-03-07
offtoppic...

Does Hyper-Threading now works? Under Ubuntu 16.04 and Xen 4.4 Hyperthreading is disabeled and from my eightcore XEON D-1541 I see 8 cores instead 16

---

