---
title: "Qemu-KVM/libvirt  - console of an Instance"
date: 2014-12-16
forum: Virtualisation
---

### Post by buntuepic on 2014-12-16
Hello,

I've Qemu-KVM/libvirt VMs running on Ubuntu 12.04 in Openstack Havana environment. I know a way using "virsh vncdisplay" to access the console of an instance. But it won't allow interactive access when you need to provide root password to run fsck. 

Other way I know is to setup "pty" using "virsh edit <vm>". But when I restart the VM, it gets overwritten.

Does anyone know a way around to get console access to be able to run fsck?

The guestmount method is not what I want to do for this purpose. I want full fledged console access.

Thanks

---

### Post by TheFu on 2014-12-17
Not certain I understand completely, but I always use virt-manager to gain console access to VMs. This tool can run from anywhere with ssh access to the hostOS. It provides a GUI for creating and management of VMs through libvirt similar to many of the other hypervisor options.

I've never used openstack, so don't know how that might interfere with this technique.

Solved?

---

