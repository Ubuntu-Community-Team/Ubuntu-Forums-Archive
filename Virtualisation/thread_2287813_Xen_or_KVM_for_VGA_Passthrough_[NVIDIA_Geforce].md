---
title: "Xen or KVM for VGA Passthrough [NVIDIA Geforce]"
date: 2015-07-22
forum: Virtualisation
---

### Post by SirTempest on 2015-07-22
I'm looking at switching away from Windows to Ubuntu on my laptop. However, I'm also a gamer at heart, and I play a lot of newly released titles, that may not have the best support on WINE. Since all the servers I administrate run Linux, and a few them are VM hosts built on Xen, I'm comfortable with a command line and virtualization, and I was looking at running Xen/KVM and running Windows in VM with VGA passthrough of the main graphics card.

However, I've heard there are issues with NVIDIA Geforce cards and VGA passthrough, and people have had sparse luck with both, and recent guides seem to consistently use KVM as the platform.

So for running a Windows gaming VM, which platform, KVM or Xen, offers better VGA passthrough support, especially with a NVIDIA Geforce card? I have no experience with KVM, since my servers are generally too old to have VT-X/VT-D, but that's not much of an issue.

Also for safety sake, here's my laptop specs:
```
CPU: Intel Core i7 4710HQ
GPU: NVIDIA Geforce 860M 4GB
RAM: 16GB DDR3 PC3-12800
HDD: Crucial 512GB SSD
```

AFAIK, I can passthrough the NVIDIA card, and leave the integrated card to run the host.

---

### Post by TheFu on 2015-07-22
Did you read the multiple threads in THIS sub-forum about doing this yet?

Both Xen and KVM are picky about the GPU for passthru.
VT-d is mandatory.

---

### Post by SirTempest on 2015-07-22
Yes. I have. I'm aware of how picky they both are, especially with Geforce. I was asking if in general I'd have better luck with one or the other.

I have VT-d as well.

I'll just use KVM, since it seems in the long run it will have better support, and most success stories and guides are written for KVM.

---

### Post by KillerKelvUK on 2015-07-24
Check are the mega Arch thread on this...the main post keeps getting updated with links to various resources that apply for Ubuntu also.  I'd recommend you research your hardware specifically and from the link below you'll find a db of tested hardware and the associated configurations.

From my reading around Xen seems more involved from a configuration and admin perspective but definitely capable in terms of passthrough, if you have direct Xen background and not KVM it may be a case of "better the devil you know".  I use KVM myself, lots of support here from members and mods.

[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)

---

### Post by grvmjain on 2015-10-13
SirTempest, did you have any luck with setting up GPU passthrough using your laptop? I'm looking to do the same with my laptop.

---

