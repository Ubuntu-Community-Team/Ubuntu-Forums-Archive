---
title: "Intel VT support for Virtual Box"
date: 2009-02-24
forum: Virtualisation
---

### Post by linfidel on 2009-02-24
Hi,

Have any of you had experience with and without VT support for virtual box?  Seems like they recommended leaving it disabled, because their code was more efficient without it, and some tests have born that out in the past.  I'm trying to decide if it's an issue, because I'm upgrading my computer to either a quad Q8200 (no VT support) or a duo E8400 (VT support).  The Q8200 is $10 cheaper, but that's not the issue.  If VT support is not a big deal, then it's a toss-up.  Actually, I don't even know if running a virtual machine is that big a deal, since I have a spare Windows system anyway. :-)  Maybe in the future it will be.

Thanks for any ideas.

---

### Post by bodhi.zazen on 2009-02-24
IMO if you are going to go for VT support take a look at KVM.

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

You can of course run KVM in Ubuntu (or any distro really).

---

### Post by linfidel on 2009-02-24
> **bodhi.zazen said:**
> IMO if you are going to go for VT support take a look at KVM.

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

You can of course run KVM in Ubuntu (or any distro really).Thanks... I looked at it.  It looks much more sophisticated than what I would need.  I only need a simple setup equivalent to VMWare's workstation software, to run Windows XP for those programs that I still require in Windows.  VirtualBox has worked very well for me in the past.

But right now, I have a windows XP system on a KVM switch, so I can switch to it quickly.  In the future, though, I may want to get rid of it completely.

I just downloaded VirtualBox's manual, and they do say that in most cases, hardware virtualization is not an advantage, although it may be enabled if there are problems with their software virtualization.

---

