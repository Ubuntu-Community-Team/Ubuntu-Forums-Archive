---
title: "VirtualBox massively outperforming KVM - comments?"
date: 2014-11-21
forum: Virtualisation
---

### Post by Lockheed on 2014-11-21
I wanted to see what would be the best performing (for my needs) virtualisation solution. I kept reading KVM outperforms VirtualBox, so I installed KVM and gave it a try. However, the guest system seems sluggish compared to VirtualBox so... I compared the two.

Host:
Core2Duo 2.5GHz, 8GB RAM, SSD
3.18 kernel, latest VirtualBox

On each VM I:
- installed the same fresh XP 32bit system
- installed appropriate guest additions
- I did NOT enable 2D acceleration on VBox, and I DID select QXL graphics on KVM (so if anything, VBox got a shorter end of the stick here)
- run Passmark benchmark.


Here are my findings:

[B]KVM / VirtualBox
[/B]
CPU Mark [COLOR="#008000"]1147[/COLOR] / 761
2D Graphic Mark 70.3 / [COLOR="#FF0000"]307.9[/COLOR]
Memory Mark [COLOR="#008000"]434[/COLOR].4 /  371.1 
Disk Mark 290.7 / [COLOR="#FF0000"]993[/COLOR]

Samba Sequential Read: 6.3 / [COLOR="#FF0000"]**84.5**[/COLOR]
Samba Sequential Write: 11 / [COLOR="#FF0000"]**40.1**[/COLOR]
Samba Random Seek + RW: 2.54 / [COLOR="#FF0000"]**44**[/COLOR]

------------------------------------------
**Overall passmark rating 298.7 / 463.4**
------------------------------------------

So it appears that apart from CPU and Memory Mark (in which KVM edges in front of Vbox) VirtualBox simply obliterates KVM. And don't even get me started on Samba share performances, where KVM does just absurdly bad.

I am quite surprised native KVM virtualisation compares that badly to VirtualBox. There either is something very wrong with KVM, or it just can't run Windows guests properly.

Any comments welcome.

---

### Post by houstonbofh on 2014-11-21
There is a lot written on improving disk performance in KVM.  Specifically caching, and using the virtuo disk device.  Virtualbox has better default disk options...  As far as graphics, virtualbox wins.

---

### Post by TheFu on 2014-11-23
Graphics performance usually doesn't matter much to people running virtual servers.  If you want graphics performance, KVM is **not** the solution, but for pretty much anything else, it is.  Virtualbox is the best of the free solutions for desktop-on-desktop virtualization.

Comparing unsupported OSes like WinXP is always a bad idea, but if that is your use-case, fine.

There are many, many, ways to tune VMs. For non-GPU related tasks, any of the VM solutions should get 90-95% of native performance, provided well-known, settings are used.  I've posted links for performance settings here many, many times.

---

