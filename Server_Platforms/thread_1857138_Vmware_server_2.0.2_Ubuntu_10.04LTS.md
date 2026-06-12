---
title: "Vmware server 2.0.2 Ubuntu 10.04LTS"
date: 2011-10-09
forum: Server Platforms
---

### Post by Sparco on 2011-10-09
I have almost a new installation, the only things i have installed is LAMP and mumble server and a new NIC Intel Pro 1000mt server duel ports. I followed this guide [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) and used the script and still getting error





```
Using 2.6.x kernel build system.
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function âVNetFilter_HandleUserCallâ:
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/root/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(
```

---

