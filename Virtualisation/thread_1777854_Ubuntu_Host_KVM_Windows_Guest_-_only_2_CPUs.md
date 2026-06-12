---
title: "Ubuntu Host KVM Windows Guest - only 2 CPUs"
date: 2011-06-08
forum: Virtualisation
---

### Post by davexl on 2011-06-08
Hi all,

I need to figure out how to configure KVM to run a Windows 7 guest with 24 threads. (dual x5680 = 2 cpus x 6 cores + Hyperthreading = 24 threads)

Right now a Windows guest sees only 2 cores - I need to pass the CPU topology correctly.

I am somewhat of a Linux newb, and after much googling I realise I am simply lost. 

[This page]("http://berrange.com/posts/2010/02/12/controlling-guest-cpu-numa-affinity-in-libvirt-with-qemu-kvm-xen/") looks like it has the answers, but implementing it has me confused.


I have also tried:

VMware vSphere install fails on an SR2 - network issues.
Virtualbox and vmware workstation have core limits.
Proxmox can't handle more than 16 cores.
Xen hypervisor needs more Linux skills than I have.

It looks like KVM or bust.

One complication is that I have to use the generic ck kernel - other linux kernels do not perform well on the SR2 for folding. I am using 10.10 ubuntu [as set up here.]("http://hardforum.com/showpost.php?p=1036935472&postcount=259")

On the bright side, if anyone can help me, then I can run folding@home full time on Ubuntu at warp speed, and still do 3D renders in the Windows host. Just imagine, you could help me cure cancer AND earn a living. ;)

---

