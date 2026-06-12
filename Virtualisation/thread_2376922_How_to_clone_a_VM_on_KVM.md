---
title: "How to clone a VM on KVM"
date: 2017-11-07
forum: Virtualisation
---

### Post by satimis on 2017-11-07
Hi all,

Host - Ubuntu 16.04 Gnome desktop
VM - Ubuntu 16.04 Gnome desktop
KVM

On VM to be cloned -> right click
-> Clone

Clone virtual machine
Storage vm (No write access)
-> Detail
"create a new disk (clone) for the virtual machine" greyout

I have checked the VM to be cloned
"show virtual hardware detail"
It seems no item related.

According to following document it seems a little bid complicate to me for cloning a VM
How To Clone and Use KVM Virtual Machine in Linux
[https://computingforgeeks.com/how-to-clone-and-use-kvm-virtual-machine-in-linux/](https://computingforgeeks.com/how-to-clone-and-use-kvm-virtual-machine-in-linux/)

Please help

Edit-1
====
If start virt-manager as root

grey disappears.  Can I clone VM in this way?

Edit-2
====
following document works for me to clone VM:

How to clone KVM-based Virtual Machines on Redhat Linux 
[https://linuxconfig.org/how-to-clone-kvm-based-virtual-machines-on-redhat-linux](https://linuxconfig.org/how-to-clone-kvm-based-virtual-machines-on-redhat-linux)

But I'm still interested to know how to do it with Virtual Machine Manager

Regards
satimis

---

