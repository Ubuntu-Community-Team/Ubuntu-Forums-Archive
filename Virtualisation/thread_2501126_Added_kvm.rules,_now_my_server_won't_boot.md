---
title: "Added kvm.rules, now my server won't boot"
date: 2024-09-23
forum: Virtualisation
---

### Post by ssm3155 on 2024-09-23
Hi all,
I've been trying to run a qemu for several days, and running into the error "qemu-system-x86_64: failed to initialize kvm: Permission denied". At first, I thought it was a simple permission error, but I'm in the kvm group.

I spent all morning reading through different forums and posts addressing this issue; In the end, I did the following:
 1. I created "/etc/udev/rules.d/99-kvm.rules" with contents:
        KERNEL=="kvm", GROUP="kvm", MODE="0660"
 2. I restarted the libvirtd service -- systemctl restart libvirtd

Now, on the next reboot, the boot drive and filesystem aren't mounting. Do you have any recommendations?

Thank you for your time

---

### Post by TheFu on 2024-09-23
Are you using virt-manager and libvirt to setup and manage your VMs or are you doing it the hard way?  KVM isn't the only group involved, BTW.  Check that your userid is in the "_libvirt_" group. That's probably more important.

I've never needed to touch any udev rules for KVM to work well.  Started using it in 2010 with KVM/QEMU + libvirt + virt-manager.

Also, be certain that /var/lib/libvirt has sufficient space for your VMs if you don't use some other backend storage solution like logical volumes. libvirt supports about 10 different storage back-ends, not all of them are file-based.

And of course, your computer needs to have vt-x or amd-v enabled in the BIOS. KVM will never work without that enabled.

---

