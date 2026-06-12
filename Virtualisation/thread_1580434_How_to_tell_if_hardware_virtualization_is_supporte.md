---
title: "How to tell if hardware virtualization is supported?"
date: 2010-09-23
forum: Virtualisation
---

### Post by memilanuk on 2010-09-23
So... how do you tell if a given box (not built from scratch, and not a high $$$ server) supports virtualization such as KVM?  Is it possible for the processor to support it but for the motherboard to not enable/allow it?

Thanks,

Monte

---

### Post by TheFu on 2010-09-24
$ egrep 'vmx|svm' /proc/cpuinfo

Yes, the motherboard must support VT-x (or whatever AMD calls their version), in addition to the CPU having specific support.  Most of the time, VT-x is controlled in the BIOS, but some manufacturers, like SONY, do not have the settings in the BIOS. This means even if your CPU model supports it, the BIOS setting cannot be enabled. You are screwed in that situation.

Also, the VT-x support will only show up in the OS physically running on the hardware, not inside any virtual machine.

---

### Post by memilanuk on 2010-09-24
> **TheFu said:**
> $ egrep 'vmx|svm' /proc/cpuinfo

I was thinking more along the lines of something I could do prior to having said parts physically in hand...

> ...the motherboard must support VT-x (or whatever AMD calls their version), in addition to the CPU having specific support.  Most of the time, VT-x is controlled in the BIOS, but some manufacturers, like SONY, do not have the settings in the BIOS. This means even if your CPU model supports it, the BIOS setting cannot be enabled. You are screwed in that situation.

My current desktop machine (HP Pavillion running Vista is like that.  Got it last summer all brandy new and after the family vacation I was all hyped to finally throw some 64-bit Ubuntu on it, as it had '64-bit' splashed all over it, ran 64-bit Vista, etc.  Turned out I can only run 32-bit OSes in virtualization, as some of the cheaper HP consumer-grade PCs lack the settings in the BIOS to make it work, as you describe.  Imagine my surprise... :(

Part of my concern stems from the move towards KVM which sounds like it's less forgiving of hardware that is lacking and away from XEN, which correct me if I'm wrong supports some paravirtualization?  I'd rather not get into a 'virtual machine host' install from the Server CD and find out that my hardware on my newest (used) mini-tower isn't going to work with KVM.  I guess my only option is to pony up for 'real' hardware - or at least stuff with a known pedigree - or stick with VboxHeadless...?

Monte

---

### Post by TheFu on 2010-09-24
> **memilanuk said:**
> I was thinking more along the lines of something I could do prior to having said parts physically in hand...

If you know the exact CPU model used, you can look up the capabilities on AMD or Intel's web sites. Here is Intel's [http://ark.intel.com/VTList.aspx](http://ark.intel.com/VTList.aspx) . Now you just need to know whether the BIOS settings let you control HW Virtualization. Only the vendor can answer that. 

Every Dell laptop or desktop that I've used did let me enable it. Also, for desktops, I build my own to reuse parts from other systems which is much cheaper. It is amazing what $400 can build.  Check out my blog for more info on building a new PC (parts) and lots on virtualization ... lots.

---

