---
title: "virtualbox error - Kernel driver not installed (rc=-1908)"
date: 2020-08-25
forum: Virtualisation
---

### Post by scott30 on 2020-08-25
Hello,
I have a new install of Ubuntu 20.04.1 LTS,  I installed vitualbox and created a virtual harddrive.
When I press start to continue the process I get this error,

Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by executing

'modprobe vboxdrv'

I have reinstalled virtualbox-dkms and used the above command and nothing, I just get,

modprobe: ERROR: could not insert 'vboxdrv': Operation not permitted

From what I have read I think it has something to do with EFI Secure Boot enabled, but not sure.
Can someone point me in the right direction?

Thanks

---

### Post by CelticWarrior on 2020-08-27
Yes, it has to do with Secure Boot. Just disable it.

---

