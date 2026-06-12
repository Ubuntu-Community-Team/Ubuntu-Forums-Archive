---
title: "How to recover a deleted VM"
date: 2010-07-17
forum: Virtualisation
---

### Post by satimis on 2010-07-17
How folks,

KVM

Accidentally I deleted a VM on the VirtualMachineManager.

VM.xml is still in /etc/libvirt/qemu/VM.xml
VM.qcow2 still in /VM/VM.qcow2

Please advise how to add it back?  TIA

B.R.
satimis

---

### Post by Dedoimedo on 2010-07-19
You did not delete the files on the disk, I presume, you merely de-registered the virtual machine from the manager, you mean?
Dedoimedo

---

### Post by satimis on 2010-07-19
> **Dedoimedo said:**
> You did not delete the files on the disk, I presume, you merely de-registered the virtual machine from the manager, you mean?
Dedoimedo

Hi,

I got my problem fixed by running;
$ sudo virsh define /path/to/VM.xml

I got the guest back on Virtual Machine Manager.  Do you know which file holding this info?  So in next time I can edit that file.  TIA

B.R.
satimis

---

### Post by Dedoimedo on 2010-07-20
I don't remember by heart.
I'll have to dig into my KVM test box and see what gives.
Dedoimedo

---

