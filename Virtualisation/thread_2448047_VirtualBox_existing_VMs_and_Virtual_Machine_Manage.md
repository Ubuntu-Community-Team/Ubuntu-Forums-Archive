---
title: "VirtualBox existing VMs and Virtual Machine Manager integration"
date: 2020-07-31
forum: Virtualisation
---

### Post by fragglebliss on 2020-07-31
I have been an avid user of VirtualBox for many years yet have only just started playing around and testing Virtual Machine Manager (QEMU/KVM).

I am currently creating a new VM inside Virtual Machine Manager for testing and so far is running fine and there are no problems.

But what I am curious of is, is there any way for Virtual Machine Manager to see the existing VMs I have installed inside VirtualBox?

I'm seeking some clarification as I'm unsure whether this is even possible and precise information is so difficult to find using search engines (and yes, I have tried).

Is it a simple case of because they're installed using two different packages that I must continue to use both VirtualBox and Virtual Machine Manager side-by-side?

Or is there some way to unite them into one GUI?

---

### Post by Dennis N on 2020-07-31
See this:

[Best practice to migrate from VirtualBox to KVM]("https://access.redhat.com/discussions/4340061")

---

### Post by fragglebliss on 2020-08-01
While I appreciate the response, the response you did provide had absolutely nothing to do with the questions that I asked. You either misread my post, or never read it at all. Since I am a polite and civil fellow Linux user, I will give you the benefit of the doubt and assume that you misunderstood my post.

So as far as I am concerned, this still remains an open thread and my questions are still unanswered.

---

### Post by TheFu on 2020-08-01
> **fragglebliss said:**
>  So as far as I am concerned, this still remains an open thread and my questions are still unanswered.

You'll probably be unhappy with my reply too.  Nobody here works for Canonical. Everyone is a volunteer.

You can reuse the VDI files. libvirt is supposed to be able to hook into virtualbox, but I've never seen that done and never tried it myself.
A web search found this: [https://libvirt.org/drvvbox.html](https://libvirt.org/drvvbox.html)  They mention some incompatible licensing between libvirt and virtualbox causing problems. I wouldn't assume that after doing that, then it would be possible to use the VirtualBox GUI again.

About 20 yrs ago, I moved all my virtualbox VMs over the KVM+qemu and libvirt control.  At the time, to get good performance it was necessary to convert from .vdi to .img files which were fully pre-allocated, i.e. not sparse files.  If you put the VDI files on fast SSDs, then that doesn't matter these days.

I don't know any method to convert the virtualbox VM configuration to a format that works for KVM+qemu other than to manually configure them. That has worked a number of times for me.

I only use virt-manager to setup VMs, never to access them unless I must have a console.  There are much more efficient ways to access VMs than the hokey VNC/Spice interface provided.  IMHO.

The link provided by Dennis N says most of that in the comments - at least to my reading. Moving existing VDI files over to be used by KVM isn't hard, but KVM is a server hypervisor, not really meant for typical desktop users.  If you move the VDI files out of a HOME directory to where libvirt expects to find them ... or add a new "storage pool" for libvirt to manage, then those files can be used directly - assuming the correct virtual hardware is configured in the libvirt setup.  But libvirt has many more powerful, faster, storage methods that a vdi supports.  I use LVM storage and have the block storage presented as needed to the different VMs.  Relatively speaking, vbox is a toy in comparison to all the advanced network and storage and RAM balloon and CPU emulation capabilities libvirt provides with qemu+kvm.  Thanks to spice, even the GUI performance is very fast compared to what we had previously, especially if access happens from the same machine where the hypervisor is running.  I never do that, but most home kvm users would, I suppose.

BTW, libvirt has been massively under development the last 10 yrs, so different versions can have extremely different capabilities.  The virt-manager GUI that I use on 16.04 is very different from the virt-manager on 20.04.  So all questions related to libvirt and virt-manager should clearly state which OS release is being used and which libvirt version.  On three different Ubuntu KVM systems:
```

ii  libvirt0:amd64   **1**.3.1-1ubuntu10.30 amd64  library for interfacing with different virtualization systems
or
ii  libvirt0:amd64   **2**.2.0-0~16.04~ppa0 amd64  library for interfacing with different virtualization systems
or
ii  libvirt0:amd64   **6**.0.0-0ubuntu8.2 amd64    library for interfacing with different virtualization systems

```

And I'm sorry if I misunderstood the question too. Maybe try explaining it differently rather than saying "that's not what I wanted."

---

### Post by fragglebliss on 2020-08-01
Thank you, your reply was great and actually went a long way to confirm what I had already thought was the case of interoperability. I appreciate your thoughtful reply.

Except for this opening statement which frankly, I have absolutely no idea why you included because I never mentioned anything to do with Canonical. But anyway, I can ignore this because the rest was great, as I mentioned.

> **TheFu said:**
> <snip> Nobody here works for Canonical. Everyone is a volunteer.

---

### Post by SeijiSensei on 2020-08-02
I've never used KVM, but can it import VMs exported in the Open Virtualization Format?  See File > Export Appliance in the VirtualBox manager.

---

