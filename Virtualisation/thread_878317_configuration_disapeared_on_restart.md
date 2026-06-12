---
title: "configuration disapeared on restart"
date: 2008-08-02
forum: Virtualisation
---

### Post by uopjohnson on 2008-08-02
I used virt-install and virt-clone to create a few windows XP instances and then I used virt-manager to connect to them, start them, stop them, etc several times.  All was good for a couple of days.  Then I rebooted and now when I try and use virt-manger to start a domain I get and error 
qemu: could not open disk image xp_sp3_ie6.img
If I use virsh list --all I get no domains listed.  These are all User domains and I can still see the configuration files in ~/.libvirt/qemu but I can't start them or access them.  I really thought I was rolling along nicely, but there is clearly something fundamental I don't understand. 
Help?

---

### Post by uopjohnson on 2008-08-02
Of course 20 seconds later I realized that the paths in the domain xml configurations in ~/.libvirt/qemu/ should probably be absolute paths so I edited those and now everything works.  I guess rebooting clears something were libvirt-bin was keeping track of the relative paths to the disk images. 
Is that a bug, or expected behavior?

---

