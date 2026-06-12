---
title: "Virtualize - Physical Hardware"
date: 2007-11-29
forum: Virtualisation
---

### Post by OmahaVike on 2007-11-29
Hello one and all,

In advance, I entirely appreciate any insight to my situation.

In the Dapper host virtualization packages I have played with (qemu and virtualbox), they seem to create their own custom hardware emulation.  What I am looking for is virtualization which bridges directly(?) to the hardware itself.  

In other words, if I have a video capture card installed, and working in the Dapper host, I'd love to be able to access that card from the virtualized environment as well.

If possible, will someone please point me to a virtualization package which supports this kind of functionality?

Once again, thanks most kindly!

---

### Post by PilotJLR on 2007-11-29
I think VMware Workstation supports 3D video card stuff (or maybe it is on the roadmap for the next version, I can't recall).

Other than that... nothing really does this. The point to virtualization is to NOT directly connect to hardware. Unfortunately the hypervisor takes away some of the good stuff for desktops!

---

