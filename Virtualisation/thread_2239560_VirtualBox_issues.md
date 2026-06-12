---
title: "VirtualBox issues"
date: 2014-08-14
forum: Virtualisation
---

### Post by jacob46 on 2014-08-14
Hey guys,

So I am very new to this world, but am trying to get a linux machine up and running for my daily work machine.  I work at a software company and it seems beneficial for me to learn linux.

Anyways, I'm trying to set up a VM for a couple little things ( I need to be able to use MS SQL server, and I need to be able to use IE (for troubleshooting etc)).  

I was suggested VirtualBox, but am encountering the error that I'm seeing others having.  That virtualbox cannot be run in a Xen Environment.

Now, I sort of understand what's going on here, but not too well.  All I can find on the internet is people being snarky and telling people they're dumb for not knowing what this means.. So I'm hoping you guys could take a second and help me understand.



Using Xen itself for my VM needs seems to be an incredibly intimidating endeavor .. So I'm trying to weigh my options. 

Is there a way for me to configure my machine (even if this means reinstalling ubuntu/switching distros) so I can use VirtualBox?  Or would tackling the monstrosity that is setting up a VM with xen a simpler solution?

I would really appreciate any help anyone can offer.  I apologize for my ubuntu-illiteracy.

Thanks!

---

### Post by sudodus on 2014-08-14
I don't know Xen, but I use VirtualBox and [KVM + virt-manager]("https://help.ubuntu.com/community/KVM/Installation").

You have probably enough disk space to dual boot, and have a dedicated Ubuntu system that can host a virtual machine, if Xen creates too much problems.

---

### Post by jacob46 on 2014-08-14
What exactly do you mean? Dual boot what?  Another ubuntu system?

---

### Post by sudodus on 2014-08-14
Yes, if Xen creates too much problems.

---

### Post by jacob46 on 2014-08-14
Well, if that's a solution, I can simply re-install ubuntu alltogether.  But I'm not sure how to do that and make sure xen isn't with the new distro.

---

### Post by jacob46 on 2014-08-14
Basically, if I'm understanding this correctly, I'm running a Xen Kernel (or my current kernel has some attachment to Xen), and I want to either change that.. or get a distro that doesn't have this connection.

When I installed Ubuntu, I didn't see anythign about xen denoted.. so I don't know how I would re-install and fix this.  Likewise, I don't know what to look for in a distro to avoid this issue.

---

### Post by sudodus on 2014-08-14
Who can help us? Can the current Ubuntu (14.04.1 LTS) run Virtualbox? What is this problem with Xen?

-o-

I'm running VirtualBox with the previous long time support version, Ubuntu 12.04 LTS (which has support until April 2017). So that may be a solution for you, if it does not work with 14.04.1 LTS.

Another solution might be that you run KVM + virt-manager, see the link in post #2.

---

### Post by TheFu on 2014-08-15
Only run 1 virtualization technology on an OS at a time. Actually, it is best to only have 1 virtualzation technology installed.  So - you need to pick - virtualbox OR Xen OR KVM.

There is good news - container VMs like LXC or UML or Docker may be run inside HVM hypervisors like virtualbox, Xen, KVM ... if you like.

I use virtualbox as a toy and only on Windows. For a few years, it was the main desktop-on-desktop solution here. I would never use it if a server was involved. Too much overhead and not as stable as other options.

I dumped Xen around 2011 - over stability issues and it refusing to boot after kernel updates.  Switched away from ESXi around the same time - the company screwed their customers.

Started migrating all VMs to KVM in 2010 - it has been fast, stable, easy to use, and enjoyable.  I'm looking at Docker for lite-container-based needs on internal-use-only machines, but don't plan to leave KVM for external facing VMs.

Ok - so with extreme, expert, care, it may be possible to run Virtualbox inside a Xen VM ... probably best for that only to be done by the developers of either tool, not you, not me. ;) I was giving a talk on KVM and a VMware engineer in the audience suggested it was possible, but not a good idea.

---

### Post by SeijiSensei on 2014-08-15
> **jacob46 said:**
> Hey guys,

So I am very new to this world, but am trying to get a linux machine up and running for my daily work machine.  I work at a software company and it seems beneficial for me to learn linux.

Anyways, I'm trying to set up a VM for a couple little things ( I need to be able to use MS SQL server, and I need to be able to use IE (for troubleshooting etc)).  

I was suggested VirtualBox, but am encountering the error that I'm seeing others having.  That virtualbox cannot be run in a Xen Environment.

What operating system were you using before?  Windows?  Why not install VirtualBox in Windows and install Ubuntu into that?

---

