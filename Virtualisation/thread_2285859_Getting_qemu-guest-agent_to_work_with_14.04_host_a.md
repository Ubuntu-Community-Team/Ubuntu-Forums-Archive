---
title: "Getting qemu-guest-agent to work with 14.04 host and guest"
date: 2015-07-08
forum: Virtualisation
---

### Post by Chris_Berthiaume on 2015-07-08
I'd like to get the qemu-guest-agent working with my 14.04 host and guest. So far I've added the qemu-guest-agent package to the guest OS and created a new virtio serial device for the guest. Now I think I've hit this bug [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1393842](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1393842), where a required directory is not created for the new serial device and the appropriate apparmor profile is not updated. It appears as though it's been fixed in 15.05 but not 14.04. Is there any way to get this fix applied to 14.04 too? I'm not sure what the process is for bug fixes like this that apply to more than one version of Ubuntu. Maybe there needs to be a new bug report specifically for 14.04?

---

