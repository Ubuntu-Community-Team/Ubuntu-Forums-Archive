---
title: "Networking and VMs.."
date: 2008-03-10
forum: Virtualisation
---

### Post by SuperBOB on 2008-03-10
Hi,

Just getting started with Ubuntu + KVM.  
I want to give each VM its own external IP

Router 192.168.1.1
Host operating system 192.168.1.10
VM #1 192.168.1.11 
VM \2 192.168.1.12

Is there a good tutorial on how to achieve this?
Thanks


UPDATE: Ok I found a tutorial here : [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) 
UPDATE : I plugged in an ethernet cable and it worked fine.  Its not working over the wireless though, argh.

I followed the part headed : "Virtual NICs Bridged Directly to Outside"

My host OS can now connect through this bridge, but the VMs can't contact the DHCP server.
I started them with -

  kvm -no-acpi -m 1024 -net nic -net tap windows.img

Is there any VM networking configuration?

Any better documentation out there?

---

