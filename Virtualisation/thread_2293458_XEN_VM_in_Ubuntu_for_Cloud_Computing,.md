---
title: "XEN VM in Ubuntu for Cloud Computing,"
date: 2015-09-05
forum: Virtualisation
---

### Post by Johnny_P on 2015-09-05
Hy,

I am interested to know if somebody know the limitation of virtual machine XEN for:

- numbers of processors or cores or threads / 1 virtual machine
- GB of memory RAM / 1 virtual machine
- number of virtual machines XEN which can be create and can be use in Cloud Computing using Ubuntu 64bit 

It is very important to specified that all this virtual machines will be use in numerical analysis (simulations) in CAE domain, so the processors, RAM's and hard-disk will be intensively use.

Thanks in advance to all comunity for support.

Keep in touch.
Best regards.

---

### Post by TheFu on 2015-09-05
The answer is *it depends.* 
There isn't any practical limit on the number of VMs any single system can have because you will run out of CPU and/or RAM first. This will probably be true for a few more years, at least, if not a decade.

There is an optimal point where having more VMs is bad. That depends completely on the workload.

If you need the absolute numbers - check the Xen website. There is nothing special about Ubuntu to change those. 1 easy web search found this: [http://wiki.xenproject.org/wiki/Xen_Project_Release_Features](http://wiki.xenproject.org/wiki/Xen_Project_Release_Features)  Some of the most important things for running lots of VMs are not officially released yet.

---

