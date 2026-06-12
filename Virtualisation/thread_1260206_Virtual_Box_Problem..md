---
title: "Virtual Box Problem."
date: 2009-09-07
forum: Virtualisation
---

### Post by chrispche on 2009-09-07
Hi there,

I'm trying to run Windows XP in Virtual Box under Ubuntu 9.04. However, after setting up the VM and then I try to run it I get:

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Can someone tell me what I need to do here. I'm not that technically minded, but I love Ubuntu over Windows any day. I just have to run XP to access some sites that require Microsoft Drivers. I digress, can anyone help please.

Thanks in advance.

---

### Post by Ocxic on 2009-09-08
run this "sudo /etc/init.d/vboxdrv setup" to make sure the vbox kernel module is installed properly, and make sure you are part of the vboxusers group.

Do so by going to "system->administration->users and groups" unlock and click manage groups,
find and select vboxusers and click properties, make sure your usersname has a check beside it making you a member of that group, click ok to everything and close out of users and groups.. logout and back in and you'll be good to go.

---

### Post by chrispche on 2009-09-08
Thanks.

---

