---
title: "UEFI vs BIOS for guest VM?"
date: 2015-09-23
forum: Virtualisation
---

### Post by zexelon2 on 2015-09-23
I am currently experimenting with Xen and have had about 85% success so far (for what I am doing I am very happy with this). The question I have is what is the difference between using a UEFI BIOS or a Legacy BIOS for booting guest VMs. 

I know there are a ton of differences between UEFI and the legacy BIOS that touch on just about every aspect of a computers hardware, however when it comes to using virtual machines is there any advantage or difference between UEFI or BIOS from a performance or ease of use? 

Can one handle hardware (VGA) passthrough better than the other? 

The only major thing i have noticed is that Xen does not yet seem to support UEFI.

Thanks for any insight!

---

### Post by TheFu on 2015-09-23
BIOS booting has been part of virtualization for .... coming on 20 yrs.  UEFI was added like 3 yrs ago. Guess which one works better, with fewer hassles?

Unless you have a strong reason to choose EUFI, don't.   Well - unless you'd like to become an expert at it.

---

### Post by zexelon2 on 2015-09-23
Okay, this is kind of what I thought. I have run into BIOS issues on real hardware (specifically running out of option rom space) but its not stuff I can ever see running into in a VM. The only place where I have consistently seen UEFI used is getting Nvidia gfx cards to work with passthrough. Apparently UEFI makes it work somehow.

---

