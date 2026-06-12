---
title: "Setting up a production KVM server"
date: 2008-12-08
forum: Virtualisation
---

### Post by gecka on 2008-12-08
Hello,

I am trying to setup a KVM server for production, referring to [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) and [https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder)

I simply want to be able to  easily create, clone and monitor resources of virtual machines using JEOS (intrepid) All my virtual machines should be accessible from external network, so I need bridge networking for each.

I installed KVM with:
> sudo apt-get install kvm libvirt-bin python-vm-builder qemu bridge-utils

Two question:
- why does build-essentials get installed ? I hate having a source compiler on a production server.
- should I use vmbuilder or virt-install as stated in official ubuntu server documentation ?

Regards.

---

### Post by Dedoimedo on 2008-12-09
To compile, you need a compiler and what not, hence the build essential packages. That's for question one. Question two, I'll think about it a little.
Dedoimedo

---

### Post by gecka on 2008-12-09
> **Dedoimedo said:**
> To compile, you need a compiler and what not, hence the build essential packages. That's for question one. Question two, I'll think about it a little.
Dedoimedo

Well I dont want to compile anything! That was qemu package that depends of build essentials. But seems it not really needed by kvm

---

### Post by Yann2 on 2008-12-10
For question 2: if you want to install Hardy or jaunty guests, vm builder. Else, virt-install :)
For question 1: good question. Don't know. Can't really remember if it did that on hardy..

---

