---
title: "afeter a kernel update I must reconfigure VMWare Tools?"
date: 2009-12-16
forum: Virtualisation
---

### Post by frankabel on 2009-12-16
Hi all,

When I installed VMware Tools I see the the installer build kernel modules again my current installed kernel. That mean that each time I update my kernel I must run the configuration script of the VMWare Tools?

Cheers
Frank Abel

---

### Post by darco on 2009-12-16
After a kernel update, vmware always rebuilds its modules automatically. The only issue I have seen is when vmware is not ready for the latest kernel and a patch must be installed before the modules will rebuild.
As far as vmware tools after a kernel update, its rare that I have had to reinstall the tools buts its so easy I am not sure why you would even ask?


darco

---

### Post by frankabel on 2009-12-16
Thanks darco.

Is easy for one machine install vmware tools, but not for more than 30 servers, beside, we are running jeos, and we don't like installed packages like build-essential and linux-headers, so each time we recompile vmware modules we need install and uninstall such packages.

So, the automatic rebuild of module work even without build-essential and linux-headers packages? 

One more question, how can I test if the vmware kernel modules are fine after a kernel update? You talk about reinstallation, but is neccessary a reinstallation? or is enough with a reconfiguration?

Cheers
Frank Abel

---

### Post by darco on 2009-12-17
> **frankabel said:**
> Thanks darco.

Is easy for one machine install vmware tools, but not for more than 30 servers, beside, we are running jeos, and we don't like installed packages like build-essential and linux-headers, so each time we recompile vmware modules we need install and uninstall such packages.

So, the automatic rebuild of module work even without build-essential and linux-headers packages? 

One more question, how can I test if the vmware kernel modules are fine after a kernel update? You talk about reinstallation, but is neccessary a reinstallation? or is enough with a reconfiguration?

Cheers
Frank Abel

Wow, more than 30 machines.....

Well I dont compile so I dont know anything about build-essentials...

Typically if the kernel stays within its family (e.g. 2.6.31.3 to 2.6.31.9) , it will not need to rebuild. When you jump to a new kernel (2.6.32) , you will be prompted to "rebuild" the vmware modules by simply clicking on the "ok" or "install" button. You will know if it fails. My modules failed w/2.6.32 but I was able to pick up a patch from the vmware forums and I am good to go.

Good luck

darco

---

### Post by frankabel on 2009-12-17
Thanks man.

---

