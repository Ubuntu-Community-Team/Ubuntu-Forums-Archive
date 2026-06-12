---
title: "Install Ubuntu Studio dualboot"
date: 2009-10-22
forum: Ubuntu Studio
---

### Post by denvro on 2009-10-22
Hello,

I have Ubuntu 9.04 installed on my pc. For music recording I want to install Ubuntu Studio next to my Ubuntu Jaunty installation. My pc standard has to boot into "normal" installation, but I want to be able to boot Ubuntu Studio.

Can anybody tell me how to make this work. Or maybe if I shouldn't do it this way please also let me know.

Kind Regards,
D.

---

### Post by trulan on 2009-10-22
Two options:
1. Install Ubuntu Studio in its own partition, or on its own hard drive.  Look for info on drive partitioning to do this.

2. Install the real time kernel and audio applications in you regular Ubuntu setup.  To do this, simply add the Ubuntu Studio metapackages using synaptic.

In either case, GRUB will let you choose which kernel to boot into.  If you want to keep all your settings and files seperate, install into a partition.  If you want all your stuff in one place, install the Ubuntu Studio metapackages.  Either way will work very well.

---

