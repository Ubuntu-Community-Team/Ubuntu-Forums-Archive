---
title: "Remote Management of KVM is driving me nuts!"
date: 2009-03-24
forum: Virtualisation
---

### Post by Schorschi on 2009-03-24
I am familar with VMware (VCP), I know Hyper-V very well (hate SCVMM), I even know Xen, and now I am working on KVM.  There are couple of things that don't make sense to me, at this point.  Just to set the stage...

3 servers, 1 Dell 2850, and 2 Dell 2950s.  I have installed 9.04 alpha 6 amd64 on all 3 servers, desktop version on 2850 (since it does not support VT, I am going to use it as my management console for virtualization.  I installed server version of 9.04 on 2950s

Installed kvm/qemu via ubuntu-virt-server bundle on the 2950s.  VT is enabled 2950s as well.  Did modprobe for kvm-intel, etc.  KVM is up and functional.  I installed ubuntu-virt-mgmt on the 2950, and virt-manager is functional.  But here is the problem...

When I use virt-manager on 2850 and connect to the 2950s running KVM/QEMU, I only get QEMU as hypervisor in virt-manager, and I can not recreate a VM via the wizard.  It never accepts the path for the ISO image for the VM OS load.  In fact the browser button is grayed out and if I type in the path all I get is "ISO path not found".

If I do to either of the 2950s, I can of course create a VM directly via kvm CLI, but even when it is running I can not see it in virt-manager on the 2850.

What took minutes to do in Xen, VMware, and even Hyper-V is driving me nuts for KVM!  I really really need remote GUI based management, I really don't want to install a GUI on the 2950s, but everything I have read or seen via GUI is an example of using KVM and virt-manager on the same box?  Come on, somewhere some one is successfully running KVM based VMs with no local GUI right?

---

### Post by lewtwo on 2009-03-26
>> Come on, somewhere some one is successfully running KVM based VMs with no local GUI right?  <<

PROXMOX .... works like a champ with a 10 minute install on baremetal. It is based od Debian Etch and KVM. If nothing else you might want to take a look at how they did things and mimic it.

---

### Post by Schorschi on 2009-03-29
I am going back to the simplist model, Ubuntu desktop directly on a 2950 with everything installed on one machine, setup a few VMs and get that stable and consistent.  I will then start working on the remote aspects, on the second 2950.  It is obvious remote use of virt-manager and libvirt is where I seem to be having issues, but until I get something working all local, things are just not as I expected them to be, I realize now, I am not attacking this problem in the right way, incremental steps to the final goal.

---

### Post by Schorschi on 2009-04-05
Ok, I got Desktop version of Ubuntu 9.0.4 beta loaded and KVM running with virt-manager.  However, on a second box with Ubuntu server 9.0.4 beta loaded and KVM installed, from the first box, running virt-manager, I still can not create a VM?  The VM creation wizard just refuses to create the VM.

---

### Post by Schorschi on 2009-04-07
Ok, Wizard working now.  Bridged networking was not 100% correct.  I now have a few Windows 2008 VMs up and running.  Now I get to tackle the fun stuff... NIC teaming under bridging, and integrating my Ubuntu based NAS (iSCSI and NFS) systems as datastores for the VMs.  Fun Fun Fun!

---

