---
title: "VMware Server 2.0 on Ubuntu 10.4 Error"
date: 2010-04-30
forum: Virtualisation
---

### Post by bradj86 on 2010-04-30
I am trying to install VMware Server 2.0 on Ubuntu 10.4 x64.  Here is the error I am getting:

```
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.
```

I have the latest generic linux header package, build-essential, gcc, g++, and xinetd.  I installed xinetd because some other posts recommended doing it.

I am stumped.  Any suggestions?  I am running a Dell Core 2 Duo.

---

### Post by bradj86 on 2010-04-30
I installed Workstation 7 without issues.

---

### Post by Peppery on 2010-05-03
Take a look at [http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/](http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/), I was experiencing the same issues but this patch fixed them.

---

### Post by TimsterC on 2010-05-28
Thanks that worked for me too.

:)

---

