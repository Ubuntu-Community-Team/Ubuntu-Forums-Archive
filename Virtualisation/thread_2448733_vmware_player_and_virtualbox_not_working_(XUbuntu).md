---
title: "vmware player and virtualbox not working (XUbuntu)"
date: 2020-08-12
forum: Virtualisation
---

### Post by ferfykins on 2020-08-12
Got these errors with virtualbox after installing and trying to setup an  instance of xubuntu with it  Kernel driver not installed (rc=-1908) The  VirtualBox Linux kernel driver is either not loaded or not set up  correctly. Please try setting it up again by executing  '/sbin/vboxconfig' as root. If your system has EFI Secure Boot enabled  you may also need to sign the kernel modules (vboxdrv, vboxnetflt,  vboxnetadp, vboxpci) before you can load them. Please see your Linux  system's documentation for more information. where: suplibOsInit what: 3  VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not  installed. On linux, open returned ENOENT.    Failed to open a session  for the virtual machine xbuntu-1.   The virtual machine 'xbuntu-1' has  terminated unexpectedly during startup with exit code 1 (0x1).    Result  Code:  NS_ERROR_FAILURE (0x80004005) Component:  MachineWrap Interface:   IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}

---

### Post by CelticWarrior on 2020-08-13
Simply disable Secure Boot in UEFI settings. Otherwise you'll have to do exactly what the error message says. It's much simpler just disabling it.

---

