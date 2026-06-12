---
title: "VMware Fusion 4.1.1 vs Unity"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nutznboltz on 2012-02-15
By default Ubuntu 12.04 attempts to use Unity (the 3D one) on VMware Fusion 4.1.1.  The results look awful.  It is possible to set the controls from the unity greeter to use 2D and that works fine but most people probably won't figure that out and will say it looks terrible.

---

### Post by dino99 on 2012-02-15
and what do you expect using virtualisation ? you might be aware of some limitations.

---

### Post by nutznboltz on 2012-02-16
This is a regression plus it got worse.  Today I found it happens on qemu-kvm when running virt-manager.

Unity should not enable 3D on any 2D-only graphics hardware.

---

### Post by effenberg0x0 on 2012-02-16
Virtualization software programmers struggle to make the Virtual Machine transparent to the guest OS. It would make no sense to work in any other way.

I use Unity 3D with a very nice performance in both vmware-player and VirtualBox. In the case of vmware-player, some work is needed in order to build and install the new vmwgfx kernel module (otherwise, 3D acceleration is impossible). I have posted a link with instructions, code and screenshots of it, including a screenshot of unity-support-test and glxgears running on vmware, in recent thread here. And I'm not aware of other virtualization software that currently enables decent 3D acceleration for a Linux guest (but certainly not KVM). 

In both VirtualBox and vmware-player, Unity 3D will only load if minimum specs are met. Otherwise, Unity 2D is auto loaded. The same way it works in real hardware.

Regards,
Effenberg

---

### Post by dcstar on 2012-02-18
> **nutznboltz said:**
> By default Ubuntu 12.04 attempts to use Unity (the 3D one) on VMware Fusion 4.1.1.  The results look awful.  It is possible to set the controls from the unity greeter to use 2D and that works fine but most people probably won't figure that out and will say it looks terrible.

"Most people" don't use Virtualization, and most of those that do are aware of the 3D limitations most VM systems have.

I run 12.04 in VMware Player 4.0.1 for testing and the initial 3D graphics are total rubbish until VMware Tools are installed in the client VM (which installs the VMware video drivers).

External parties like VMware will not make their systems fully 12.04 compatible until well after the official 12.04 release date, so any issues at this stage are just bad luck and not anything the 12.04 developers can do anything about.

---

### Post by prusswan on 2012-02-18
It's okay just a little sluggish with artifiacts occasionally. I see little point in Unity 3D for a VM although I must say that the 3D performance of 10.04 is better than 12.04 in a VM, but that's hardly a surprise.

---

