---
title: "Disconnect .iso from VM cdrom"
date: 2020-11-15
forum: Virtualisation
---

### Post by ttrakker on 2020-11-15
Hi, In the image below there is a button to disconnect the iso on the guest vm. How can achieve the same with the terminal? Thanks

[ATTACH=CONFIG]287361[/ATTACH]

---

### Post by TheFu on 2020-11-15
First, virt-manager can be run from any workstation on the network that has ssh access. It doesn't need to be run on the KVM/libvirt hardware directly, so you don't need to use the CLI, unless that really is your goal. Just install virt-manager on another workstation with a GUI, then setup the connection over ssh+qemu to the KVM hypervisor host. Bob's your uncle.

Ok, so assuming you still want to use a terminal, you can use **virsh edit {VM-name}** to modify a shutdown VM settings.  Find the lines with the CDROM/DVD iso file and remove that stanza.  Then start the VM and it won't be there.  The VM-name is case sensitive, BTW.

---

