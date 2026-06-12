---
title: "Router/switch as a VM:  Kernel requirements?"
date: 2013-11-27
forum: Virtualisation
---

### Post by 1clue on 2013-11-27
Hi,

I have an i7 that has slowly become mostly a kvm/qemu host.

I put a 4-way ethernet card in and got them all working, but since it's currently an Xubuntu install I couldn't get routing or masquerade working.

In any case I don't want the virtualization host to be the router directly.  So my intent is this:
[LIST=1]
[*]Reinstall with a bare bones minimal kvm/qemu host OS, possibly server 12.04.
[*]Add an Xubuntu VM so I have a GUI, and give it my video card and such.
[*]Add a full-featured router VM and give it my 4-way video card.  And maybe the on-board one too.  I'm thinking maybe pfSense.
[*]Add a bunch of other VMs as I have need.
[*]I want the host to see exactly one network interface, and that would probably best be a virtual pipe from "inside" a secure firewall, inaccessible from outside.
[/LIST]

So I guess here are my questions:
[LIST=1]
[*]Does the VM **host** require the same advanced TCP/IP kernel features as the the router **guest**?  I think not, but I'd like to be sure.
[*]Do I have to define the NICs in the host and then donate them somehow to the guest?
[/LIST]

More information:
[LIST=1]
[*]I need advanced router features:
[LIST=1]
[*]VLANs (802.1q: REAL vlans)
[*]SPI firewall
[*]Access rules for each VLAN, including between internal networks.
[*]Multiple VPN endpoints (not just pass-through) with good performance.
[LIST=1]
[*]Allow an endpoint to appear inside of an internal VLAN
[*]The endpoint should be isolated from the rest of the network based on firewall rules.
[/LIST]

[*]IPV6 tunneling.
[*]More.
[/LIST]

[*]I have a Linksys EA6500 and have tried DD-WRT on it.
[LIST=1]
[*]DD-WRT is inconsistent, buggy and absolutely out of the question.
[*]I've tried it on several occasions including recently, and it comes up short every time.
[*]SOHO routers are too slow to do what I need.
[*]I intend to hook the EA6500 up to one of the ports and give it a VLAN.  It will be isolated from more secure VLANs.
[/LIST]

[*]Once I get this working, I'll get one or two more 4-way NICs.
[/LIST]

---

### Post by bashiergui on 2013-11-27
> 1. Does the VM host require the same advanced TCP/IP kernel features as the the router guest? I think not, but I'd like to be sure.2. Do I have to define the NICs in the host and then donate them somehow to the guest? To answer 1 I would say no if you bridge the VM. The host won't be doing anything aside from hosting the VM.
Answering 2, the router VM needs to own one of the NICs exclusively. 

I don't know what you mean by "I don't want the virtualization host to be the router directly." Do you want it to be the primary router? 

You will probably find a bunch of blogs and tutorials on how to set up a router in a VM using VMWare and VirtualBox, you might have to use one of thise and adapt it to kvm/qemu. This one seemed to address a couple of your concerns [http://www.neowin.net/forum/topic/1147046-running-my-router-as-a-vm-inside-esxi/](http://www.neowin.net/forum/topic/1147046-running-my-router-as-a-vm-inside-esxi/)

---

### Post by 1clue on 2013-11-28
The virtual router will be the primary router.

I want the KVM/QEMU host to have barely enough to handle LVM/RAID and virtualization.  I do not want it to have access to a physical NIC.

I want the router (pfSense or similar) to have exclusive access to all the physical NICs.  I want it to have only enough software to do its job, and preferably not have something like an SSH client with which to connect to other hosts in an interactive session.

Thanks.

---

