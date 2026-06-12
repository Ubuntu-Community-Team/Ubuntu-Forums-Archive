---
title: "Problem using ubuntu-vm-builder"
date: 2008-07-18
forum: Virtualisation
---

### Post by stmurray on 2008-07-18
I am trying to make the move from vmware, and am trying to get KVM to work.  I am trying to create a hardy VM using ubuntu-vm-builder:

```
ubuntu-vm-builder kvm hardy --arch 'amd64'  --mem '256'  --rootsize '4096'  --swapsize '1024'  --kernel-flavour 'generic'  --hostname 'VmHardy1'  --domain 'MurrayDomain'  --mirror 'http://archive.ubuntu.com/ubuntu'  --components 'main,universe'  --libvirt qemu:///system 

```

When I start the virtual machine created by this, I am at a grub prompt.  After some exploration in grub, it appears that no linux kernel has been loaded.

Going through the u-v-b output I find the error:
E: Couldn't find package linux-generic

When I run u-v-m without the --kernel-flavour parameter, I get the error:
E: Couldn't find package linux-server

Are these the packages that have the kernel files?  Am I doing something wrong?

---

### Post by stmurray on 2008-07-18
Never mind, I figured it out.  I had to add "restricted" to the "--components" parameter as in "--components 'main,universe,restricted'".  Seems odd that the kernel files would be in the restricted libraries, but the machine created correctly, after I made that change to the ubuntu-vm-builder command

---

