---
title: "Ubuntu Natty, Radeon and VMware Player crash"
date: 2011-07-17
forum: Virtualisation
---

### Post by cchip on 2011-07-17
Hi all,

I'm wondering if anybody here is running Ubuntu Natty, VMware Player 3.1.4 and a radeon graphics card successfully? For me, VMware usually freezes or crashes (with glibc detecting memory corruption when running vmware-vmx) when I try to play a VM.

This issue seems to be related to the radeon driver. If I change to the xorg fbdev driver (in xorg.conf) VMware works fine. Also, if I change to the vesa driver (and radeon.modeset=0 for kernel) VMware works. However, with the radeon driver VMware just crashes. I've tried options such as NoAccel "on" in xorg.conf, but those didn't help.

I have integrated AMD RS780 chipset and Natty uses the radeon r600g driver. I've tried current Debian testing (=wheezy) as well, but it has the exact same problem.

---

### Post by betor3 on 2011-08-18
Hey:

I have the same problem here. Using the Vesa driver solves the problem although we loose the benefits of the radeon driver. Since Im running Natty with gnome-shell I cant use fglrx either (separate problem).

Have you come up with another solution?

There's a post about this exact problem at the VMware community site as well: [http://communities.vmware.com/thread/322640](http://communities.vmware.com/thread/322640)

cheers,
beto

---

