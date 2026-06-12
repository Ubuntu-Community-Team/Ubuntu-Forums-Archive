---
title: "VMWARE Server Config Problem"
date: 2008-03-19
forum: Virtualisation
---

### Post by billgates456 on 2008-03-19
I upgraded my system from 6.06 to 7.10 and now I have the problem in vmware-config.pl.

When I run the vmware-config.pl the following error comes


Your kernel was built with "gcc" version "4.1.2", while you are trying to use
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and
VMware Server may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.1.3" anyway? [no] 

Please give me some solution for this

billgates456
thanks

---

### Post by dcstar on 2008-03-21
> **billgates456 said:**
> I upgraded my system from 6.06 to 7.10 and now I have the problem in vmware-config.pl.

When I run the vmware-config.pl the following error comes


Your kernel was built with "gcc" version "4.1.2", while you are trying to use
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and
VMware Server may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.1.3" anyway? [no] 

Please give me some solution for this

billgates456
thanks

Check your repositories are set to use **gutsy** and then update your system to the current packages.

---

### Post by billgates456 on 2008-03-27
I already did that thing

Still I have the problem regarding this.

Please help me

Thanks
billgates456

---

### Post by billgates456 on 2008-03-27
I think nobody know the solution here

billgates456

---

