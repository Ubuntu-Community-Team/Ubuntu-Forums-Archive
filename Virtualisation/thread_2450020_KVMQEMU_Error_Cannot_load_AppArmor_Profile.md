---
title: "KVM/QEMU Error: Cannot load AppArmor Profile"
date: 2020-09-06
forum: Virtualisation
---

### Post by Zack McCool on 2020-09-06
I recently built a new Ubuntu 20.04 server, to use as a KVM hypervisor as well as an LXD host.

I am having a problem when attempting to install a new Guest OS in virt-manager. The iso image of the install media is in /home/joe/Downloads, though I have also tried copying it to /var/lib/libvirt, and still receive the same error.

cannot load AppArmor profile 'libvirt-4c7c8492-e388-48dc-b97d-d186c8dc1dd1'

Any assistance would be terrific, the google results haven't been all that helpful thus far...

---

### Post by ramseybrenner on 2020-09-11
maybe check over the guide and see if you missed any steps:
[https://ubuntu.com/server/docs/virtualization-libvirt](https://ubuntu.com/server/docs/virtualization-libvirt)
There's a bit at the end that goes over apparmor, and will give you a good idea of where to start looking to fix the issue.

---

