---
title: "VMware Workstation 9 / 13.10 - Kernel Modules Updater Fail"
date: 2013-08-26
forum: Virtualisation
---

### Post by zakeen on 2013-08-26
Ive installed VM Workstation 9 on 13.10. It says install went well. When I start the application I get a dialog box stating:

VMware Kernel Module Updater
Before you can run VMware, several modules must be compiled and loaded into the Kernel.

choices are "cancel" or "Install"

I click on install and nothing happens.

Any ideas?

---

### Post by zakeen on 2013-08-28
Anybody?

Or was installing 13.10 the wrong way to go?

---

### Post by dhunt84971 on 2013-08-28
Try running it under sudo, like this:

sudo vmware-modconfig --console --install-all

---

### Post by xyepblra on 2013-11-06
> **dhunt84971 said:**
> Try running it under sudo, like this:

sudo vmware-modconfig --console --install-all
I followed your advise and after a long, long text I see:
```
make: *** [vmnet.ko] Error 2
make: Exiting `/tmp/vmware-root/modules/vmnet-only'
Unable to install vmnet
```

---

### Post by priyaafsar on 2013-11-07
So do I come the same problem.

---

### Post by priyaafsar on 2013-11-07
When I input the command, come the problem:
cc1: some warnings being treated as errors
make[2]: *** [/tmp/modconfig-SQGFHL/vmci-only/linux/driver.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/tmp/modconfig-SQGFHL/vmci-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [vmci.ko] Error 2
make: Leaving directory `/tmp/modconfig-SQGFHL/vmci-only'
Unable to install all modules.  See log for details.

---

### Post by nalink on 2013-11-13
Need to install 3 patches.
The following link provides the solution:[URL="https://communities.vmware.com/message/2282385"]
https://communities.vmware.com/message/2282385[/URL]



Also, might need to do this to start up vmware workstation:

pkill -f vmware-hostd

Picked up from here:
[https://communities.vmware.com/thread/460789](https://communities.vmware.com/thread/460789)

---

### Post by suhongdoan on 2013-11-26
Hi all,

There is an update for workstation 9 (9.0.3 build-1410761) that works with Ubuntu 13.10.
shd

---

