---
title: "Having trouble selecting a virtualization solution"
date: 2008-05-05
forum: Virtualisation
---

### Post by Replicon on 2008-05-05
Hi there!

Well, you know the drill... for some software, Wine Is Not Enough (see what I did there? HAH!) :D

In any case, I see there is lots of useful information in the stickies about all the options available, but I'm surprised there isn't a sticky (or a link within a sticky) dedicated to choosing a virtualization solution. There probably actually is, but I didn't search hard enough - feel free to school me.

I found the comparison page on Wikipedia: 

[http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

But that's overwhelming to say the least. So, is there a clear winner for the home user that just wants to setup a small win2k install and throw some software at it, or are they all equally good, with the selection being more of a "vim vs. emacs"-type religious battle? Free is required, of course, though I'll pick closed source over open source if there's an obvious performance gain to be had from it.

Oh yeah, and are the vmware serial numbers free? I see there's a form, but it might take you to a payments page...

cheers

EDIT: I guess it's not _that_ overwhelming... It seems to come down to VirtualBox vs. VMWare.

---

### Post by Eil on 2008-05-05
VMWare Server serial numbers are free, but you have to register to get them. I believe you can provide fake info, though.

I panned VirtualBox when I looked at it because the cool features are only available in the proprietary version (USB support and RDP to the console, I think...) But depending on what you want to do, it might be a viable option.

I read with great interest that Hardy was going to support KVM, a virtulization solution like Xen except that the hypervisor _is_ the kernel instead of a layer on top of it. Unfortunately, the userspace tools for KVM are still quite lacking. While setting up KVM guests is not terribly hard, neither is it a point-and-click affair yet.

I expect (or hope, rather) that the Ubuntu developers see this as something they can eventually use as marketing leverage. "Install Ubuntu and get everything you need to run Windows right alongside it on the same machine!"

---

