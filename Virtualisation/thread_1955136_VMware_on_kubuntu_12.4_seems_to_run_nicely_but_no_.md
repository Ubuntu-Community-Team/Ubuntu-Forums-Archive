---
title: "VMware on kubuntu 12.4 seems to run nicely but no windows."
date: 2012-04-09
forum: Virtualisation
---

### Post by commodore VC20 on 2012-04-09
I compiled the modules with the correct patch from weltall's blog (for kernels 3.2+). Everything seems to have worked nicely. Starting 'vmware' from a console i get a warning about the GTK theme engine not being in the path, but apart from that all the modules list seems to be peachy.

However, although ps seems to indicate that all works as designed, i never get a vmware window to actually show up on my screen.

Any hints or pointers welcome. I can supply various logfiles, but haven't for now as none of the ones i could think of indicate any problem at all.

---

### Post by commodore VC20 on 2012-04-10
Still couldnt figure out the problem; thought i'd provide some more info:

Latest Vmware Workstation 7 on Kernel 3.2.0-22-generic.

output when starting vmware from a console:

> (vmware-modconfig:2562): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",
filename:       /lib/modules/3.2.0-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9869FFF2EA6B02360609EC6
depends:        
vermagic:       3.2.0-22-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-22-generic/misc/vmnet.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Networking Driver.
author:         VMware, Inc.
srcversion:     3C9DAEA3611CBF112C281AE
depends:        
vermagic:       3.2.0-22-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     BCAE10A6FFA68B7A1A93708
depends:        
vermagic:       3.2.0-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-22-generic/misc/vmci.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     AF0065C2AA6B67906F2173C
depends:        
vermagic:       3.2.0-22-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-22-generic/misc/vsock.ko
supported:      external
license:        GPL v2                                                                                       
version:        1.0.0.0                                                                                      
description:    VMware Virtual Socket Family                                                                 
author:         VMware, Inc.                                                                                 
srcversion:     CAEDBF81E2A76B434419B12                                                                      
depends:        vmci                                                                                         
vermagic:       3.2.0-22-generic SMP mod_unload modversions                                                  
filename:       /lib/modules/3.2.0-22-generic/misc/vmmon.ko                                                  
supported:      external                                                                                     
license:        GPL v2                                                                                       
description:    VMware Virtual Machine Monitor.                                                              
author:         VMware, Inc.                                                                                 
srcversion:     9869FFF2EA6B02360609EC6                                                                      
depends:                                                                                                     
vermagic:       3.2.0-22-generic SMP mod_unload modversions                                                  
                                                                                                             
(vmware-tray:2587): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",              
     

output of 'ps aux | grep vmware':

> root      1151  0.0  0.0  25288  1624 ?        Ss   13:06   0:00 /usr/bin/vmware-usbarbitrator
root      1270  0.0  0.0  11504   488 ?        Ss   13:06   0:00 /usr/bin/vmnet-dhcpd -s 6 -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1
root      1279  0.0  0.0  11504   492 ?        Ss   13:06   0:00 /usr/bin/vmnet-dhcpd -s 6 -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
root      1282  0.0  0.0   9368   956 ?        S    13:06   0:00 /usr/bin/vmnet-natd -s 6 -m /etc/vmware/vmnet8/nat.mac -c /etc/vmware/vmnet8/nat/nat.conf
hero      2559  0.5  1.1 228332 44620 pts/0    S+   13:12   0:00 /usr/lib/vmware/bin/vmware
hero      2587  0.4  0.9 315012 36012 pts/0    Sl+  13:12   0:00 /usr/lib/vmware/bin/vmware-tray poweredOn


To me that looks as if everything was just peachy. Yet, i don't have that familiar vmware window popping up. I feel pretty retarded about it and would really welcome all ideas or pointers anyone might have to offer.

---

### Post by commodore VC20 on 2012-04-12
This thread can be closed as i ran the same vmware under gnome and it starts up just fine. Seems the problem is indeed the oxygen theme engine warning, so i'll take this to the approbiate subforum.

---

### Post by dzponce11 on 2012-04-19
odd.

---

### Post by dzponce11 on 2012-04-19
What is the point of all these gtk's?

---

