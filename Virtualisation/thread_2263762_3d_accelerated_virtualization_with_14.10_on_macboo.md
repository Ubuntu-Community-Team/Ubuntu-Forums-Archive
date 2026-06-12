---
title: "3d accelerated virtualization with 14.10 on macbook 11,1 (Intel Iris Graphics 5100)"
date: 2015-02-03
forum: Virtualisation
---

### Post by binaryanomaly on 2015-02-03
Did someone manage yet to get KVM, vmware or virtualbox running  including 3D-acceleration on ubuntu 14.10?
I'm on a macbook 11,1  (2014) with Intel Core i7-4578U and Intel Iris Graphics 5100.

  
I need it to be able to run my work windows VM from within Ubuntu. I couldn't get VMWare or KVM to work with 3D-acceleration so far. Is 3D-acceleration possible with that hardware at all?

It currently prevents me to switch to Ubuntu as my main OS.
Thanks for any hints.

---

### Post by TheFu on 2015-02-03
In virtualbox, there is a 3D accel checkbox in the video tab, but realize this only works after the "guest additions" have been installed successfully.  Under KVM, only QXL video using Spice will come close to this performance.  Can't say anything about VMware - they make 6 different virtualization tools - might help if you said which 1 you were using.

Without hardware passthru, the guest OS only sees virtual hardware - that is the point of virtualization.

If you really need graphics performance, video passthru is the only way and it requires a dedicated GPU for the guest, specific BIOS, specific chips and a specific kernel options compiled for VT-d support.  Don't think most laptops can do it. Using video passthru is non-trivial. There's a thread here about it.

---

### Post by binaryanomaly on 2015-02-03
Thanks for your explanation. Maybe I should point out that I do not need raw power 3d-acceleration just enough to run windows 7 with aero. So the passthrough may not be needed, just support for normal 3d-acceleration within the VM with the host having an intel iris 5100. On OS X this is no problem with Parallels and VMWare.

---

### Post by TheFu on 2015-02-03
The host GPU means ZERO inside a VM. Did you enable 3D support in the video settings and install the guest additions? Until that happens, nothing can improve.

Regardless, I would disable aero and be happier. If you want "cheese", running inside a VM is not for you.

---

### Post by binaryanomaly on 2015-02-03
I think I likely found the solution. The Mesa Project drivers that come with Ubuntu 14.10 seem not to be supported by VMWare for 3D-acceleration. Most likely it would work with the intel drivers [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) which again do not install on 14.10 but only on 14.04. I have to reinstall from scratch with 14.04 to finally verify it or wait for 15.04, the next LTS.

---

### Post by TheFu on 2015-02-03
15.04 is NOT an LTS release.
If you cannot update the OS every 6 months until 16.04 is released, then you should install 14.04.

---

### Post by binaryanomaly on 2015-02-03
Ah true. Seems anyway that the intel guys are just a release behind but not really limited to LTS as I first suspected. That makes things better.

---

