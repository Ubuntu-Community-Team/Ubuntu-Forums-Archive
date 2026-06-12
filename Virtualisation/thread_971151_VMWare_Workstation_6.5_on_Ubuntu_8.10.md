---
title: "VMWare Workstation 6.5 on Ubuntu 8.10"
date: 2008-11-04
forum: Virtualisation
---

### Post by weller on 2008-11-04
Hi!
I just upgraded to Ubuntu 8.10 and as VMWare Workstation 6.5 was also released recently I installed this, too.

Problem:
```
andreas@notebook:/etc/vmware$ sudo vmware-config.pl 
Unable to find the database file (/etc/vmware/locations)

Execution aborted.

```

When I start VMWare I get the following messages:
```
andreas@notebook:/etc/vmware$ vmware
Logging to /tmp/vmware-andreas/setup-15585.log
filename:       /lib/modules/2.6.27-7-generic/misc/vmmon.ko
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     96CBF0250D0FB3F01BFBFFC
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
filename:       /lib/modules/2.6.27-7-generic/misc/vmnet.ko
license:        GPL v2
description:    VMware Virtual Networking Driver.
author:         VMware, Inc.
srcversion:     EC3F3B7348D1089CD1F884C
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
filename:       /lib/modules/2.6.27-7-generic/misc/vmblock.ko
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     768B08090715A2D8C721BF3
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.27-7-generic/misc/vmci.ko
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     F400DF976CFE388EBC1A0A2
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
filename:       /lib/modules/2.6.27-7-generic/misc/vsock.ko
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     EC2E0BE1F6FB039D1109ADB
depends:        vmci
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
filename:       /lib/modules/2.6.27-7-generic/misc/vmmon.ko
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     96CBF0250D0FB3F01BFBFFC
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 


VMware Workstation Error:
VMware Workstation is installed, but it has not been (correctly) configured for your running kernel. To (re-)configure it, your system administrator must find and run "vmware-config.pl". For more information, please see the VMware Workstation documentation.

Press "Enter" to continue...

andreas@notebook:/etc/vmware$ 

```

Any ideas?


Regards,
  Andreas Weller

---

### Post by tregeagle on 2008-11-04
Have you tried running the config script?
> sudo /usr/bin/vmware-config.pl

Hopefully it'll work for you. 
It doesn't for me - make fails, "Unable to build the vmmon module." then refers me to one of the following pages:
[http://www.vmware.com/download/modules/modules.html](http://www.vmware.com/download/modules/modules.html)
[http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html](http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html)

Looks like 2.6.27-7-generic is not yet supported...

---

### Post by weller on 2008-11-05
No vmware-config.pl doesn't work - I already tried this:
```
andreas@notebook:~$ sudo vmware-config.pl 
[sudo] password for andreas: 
Unable to find the database file (/etc/vmware/locations)

Execution aborted.

andreas@notebook:~$ which vmware-config.pl 
/usr/bin/vmware-config.pl

```

---

### Post by shekhark on 2009-03-09
This is a problem with upgrading from a previous version. Delete (or move) your existing /etc/vmware directory and try reinstalling vmware-workstation. You shouldn't need to run vmware-config.pl. This worked fine for me, and I've got workstation 6.5 amd64 running on Ubuntu 8.10 amd64. :)

---

