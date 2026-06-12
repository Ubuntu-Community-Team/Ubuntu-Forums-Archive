---
title: "qemu/kvm Hook script for Guest restart"
date: 2019-01-02
forum: Virtualisation
---

### Post by thobittner on 2019-01-02
Hi,

I would like to setup a qemu/kvm windows guest on a lubuntu host. The aim is to run the windows guest to be used by the user and using the Linux host to reset the windows machine on boot/reboot. 

The windows would be able to use the dedicated graphics card with pci passthrough so the setup would be transparent to the user.

The following points are already working:


[LIST]
[*]pci passthrough
[*]Reset of VM drive at boot (using Hook scripts)
[*]shutdown of Linux on windows shutdown (using hook scripts aswell)
[/LIST]

Unfortunately the last thing I need I was not able to find a solution for.

I need to reset the VM drive also on reboot of the windows host. Unfortunately I did not find any possibility to inform the host about any reboot event of the guest system.

I would like not to use any script or setup in the Windows guest but only script in the Linux Host.

Is there any possibility with qemu/kvm/libvirt to have a hook script or something run when the windows guest is rebooting?

Any advice would be appreciated.

Best regards
THomas

---

### Post by TheFu on 2019-01-03
I would make an LVM snapshot before the guest started, then simply revert to that, dropping all changes, until the guest was stopped.

---

