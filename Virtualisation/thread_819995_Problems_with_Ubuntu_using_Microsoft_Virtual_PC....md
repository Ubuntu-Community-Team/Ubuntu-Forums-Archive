---
title: "Problems with Ubuntu using Microsoft Virtual PC..."
date: 2008-06-05
forum: Virtualisation
---

### Post by ardvark71 on 2008-06-05
Hi...

I can get Ubuntu to install and connect to the internet on MVP without a problem. My problem is...

Ubuntu sees my Radeon Express 200M graphics chip as an old S3 Trio, two *very* different chipsets. ;) This was obtained using    the safe graphical option in the initial setup screen. Not using that option got me something that some would consider psychedelic. I also had no 3D rendering and slightly choppy mouse movements.

Where is the safe graphical option in 8.04's setup screen and how do I get Ubuntu to correctly see my hardware in a virtual environment? MVP did not let me use the hardware assistance option, or whatever it was called, to help get the correct identification.

Also, is there good virtual machine software that will give me more option than what Microsoft's program does for free?

Best Regards...

---

### Post by bradmkjr on 2008-06-06
First the good news, there are much better products out there. Virtualbox and VMware both have free versions of some of their software which will be better then MVP. 

The bad news is you are using Virtualization, that means the hardware is virtualized to the expected lowest common denominator to work with the largest variety of software. Your fancy "Radeon Express 200M graphics chip" probably doesn't have drivers in about 1/2 of the operating systems people want to virtualize compared to the simple s3 card. Some products like VMware workstation and Parallels Workstation are offering some level of 3d support, but both those products are not free, they do have demos and feel free to download them to test it out.

Good Luck,
Bradford Knowlton
[http://x8v.com](http://x8v.com)

---

### Post by ardvark71 on 2008-06-06
> **bradmkjr said:**
> Your fancy "Radeon Express 200M graphics chip" probably doesn't have drivers in about 1/2 of the operating systems people want to virtualize compared to the simple s3 card. 

Hi Brad...

Thank you for your reply. I kind of figured as such but I thought there might be a way around it....to get the virtual OS to see the  correct chipset and to use the correct virtual driver. :biggrin:

Thanks, also, for your tips concerning VMware and Parallels, I'll have to take a look at those.

Best Regards...

---

