---
title: "vmware workstation won't open"
date: 2011-05-16
forum: Virtualisation
---

### Post by seth556 on 2011-05-16
I just got Vmware workstation installed and patched so the kernel modules are built. Now I can't open it.

Using the "vmware" command at the terminal I get a print out of different things and then it ends. No gui opens or anything useful.

Here's a sample of the code it spits out (didn't seem to give any explanation of why it isn't opening).

```
vermagic:       2.6.38-8-generic-pae SMP mod_unload modversions 686 
filename:       /lib/modules/2.6.38-8-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     B8D923FF9D00EB37F6551E3
depends:        vmci
vermagic:       2.6.38-8-generic-pae SMP mod_unload modversions 686 
filename:       /lib/modules/2.6.38-8-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     DA3F4C41B9E6F214D8E149B
depends:        
vermagic:       2.6.38-8-generic-pae SMP mod_unload modversions 686 

```

---

### Post by ursaiz on 2011-05-22
Hello,

I resolve the same problem upgrading to VMware Workstation 7.1.4 .

---

