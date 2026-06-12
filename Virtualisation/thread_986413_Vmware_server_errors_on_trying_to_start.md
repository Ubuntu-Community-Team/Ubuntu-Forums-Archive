---
title: "Vmware server errors on trying to start ??"
date: 2008-11-18
forum: Virtualisation
---

### Post by Julian David Pitt on 2008-11-18
When I try to run Vmware it will not start and if I try to run vmware-config.pl I get the following error

```
/tmp/vmware-config0/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.
```

Thanks for any help you may be able to give me everyone reading this!

---

### Post by bodhi.zazen on 2008-11-18
What version of Ubuntu ? What version of VMWare ? Server ? Workstation ?

---

### Post by Julian David Pitt on 2008-11-19
> **bodhi.zazen said:**
> What version of Ubuntu ? What version of VMWare ? Server ? Workstation ?

Intrepid Ibex, Vmware server version 1.0.6.91891, hope this helps and thank you for trying.

---

### Post by bodhi.zazen on 2008-11-19
Try this : [http://ubuntuforums.org/showthread.php?t=966070](http://ubuntuforums.org/showthread.php?t=966070)

I do not know if it will work with 1.0.6 or if you will need 1.0.7, have not tested 1.0.8 yet either , lol.

---

