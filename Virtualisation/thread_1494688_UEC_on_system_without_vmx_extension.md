---
title: "UEC on system without vmx extension"
date: 2010-05-27
forum: Virtualisation
---

### Post by dragos2 on 2010-05-27
I want to setup a cloud using 2 systems with an Intel E5200 processor which does not have Intel VT (from live cd I checked using kvm-ok and grep vmx /proc/cpuinfo).

I want to setup this cloud with UEC from 10.04 version but as far as I know UEC is kvm based and kvm can' t work without a VT enabled processor.

Although I read that Xen can work either the case (it uses an emulator when VT is not present).

Now the question is: can I setup the cloud using UEC from 10.04 ?

---

