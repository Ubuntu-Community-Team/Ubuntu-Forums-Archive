---
title: "Some tips about compatibility before proceed with setup?"
date: 2011-04-23
forum: Virtualisation
---

### Post by Fred2040 on 2011-04-23
Hi people, I have an ubuntu instalation ready to fly... and I need to do a VMware test or something relative. Then, I want to  know something important.. If I make a Windows Virtual Machine, can this  VM run StarCraft2?
As you can see, it's about use maximum resources  with graphics cards...  and not at all with CPU, and no only for games, apps like  for example 3dmax and render are needed too..
Is VMW fully compatible with OpenGL 2,3 or 4, and/or DirectX 9,10?

*Plus: Who is better KVM vs VMWare vs VirtualBox vs Others?

Thks alot srs!
Best Regards

---

### Post by HolgerB on 2011-04-26
You give no further infos on your system specs. So my answers are vague and YMMV :P

> **Fred2040 said:**
> 
... and I need to do a VMware test or something relative. 
Then, I want to know something important.. If I make a Windows Virtual Machine, can this VM run StarCraft2?
As you can see, it's about use maximum resources with graphics cards... and not at all with CPU, and no only for games, 
apps like for example 3dmax and render are needed too..
Is VMW fully compatible with OpenGL 2,3 or 4, and/or DirectX 9,10?

Well, for 3D acceleration IMO VMWare (beside Parallels Desktop, which is only available for Mac) is still king of the hill. KVM does not provide any 3D support.
Be it OpenGL or D3D. For VMWare you could either use VMWare Viewer plus some config file generator or watch out for the latest VMWare Workstation.

Mind you that any sort of emulation / Virtualisation comes at some speed impact. WINE still means the lowest speed impact to run Windows applications under Linux.
Sometimes a dual boot Linux / Windows is the best approach. Virtualisation is a great tool if you understand its limits and know how to use it.

> **Fred2040 said:**
> 
*Plus: Who is better KVM vs VMWare vs VirtualBox vs Others?

Depends on your use case. IMO KVM does good for most common desktop stuff (e.g. running a Windows VM to use old Windows software). Best of all: It's free and part of the Kernel. Even bigger companies such as RedHat use KVM for Desktop virtualisation (RHEV).
VMWare provides top notch 3D acceleration but is not for free unless you stick to the VMWare viewer plus config file tool method.
VBox (the commercial version) is in between with mediocre 3D features plus some bonus to KVM (RDP server, USB support).
Others might be better (Parallels Desktop) but are not available for Linux.

If you want more infos then simply search youtube for Parallels Desktop (latest Version) or VMWare. My experiences with VBox and 3D acceleration is somewhat old though. May be things have changed.

---

### Post by Fred2040 on 2011-04-29
WHoa! Amazing response.
If it appears that still we can not use 3D in their maximum resources ..
But enough so that some programs run well. And excellent.
Actually I am very grateful. I did not expect a comprehensive answer.
100000 Thks!

---

### Post by HolgerB on 2011-04-29
You are welcome !

I just digged out the old review of ars technica on Parallels Desktop 6:
[http://arstechnica.com/apple/reviews/2010/09/parallels-desktop-6-the-ars-review.ars](http://arstechnica.com/apple/reviews/2010/09/parallels-desktop-6-the-ars-review.ars)

Check out the review to see the performance which is actually possible inside a VM.

It is really a pitty that their PC based products do not provide such a 3D acceleration. VMWare on the other hand is not bad at all:
[http://www.youtube.com/watch?v=FgL9yX9-u5k](http://www.youtube.com/watch?v=FgL9yX9-u5k)

I guess all this will change once we get technology similar to IOMMU / VT-D which lets you reach through physical PCIe devices to the guest. AFAIK both KVM and Xen already provide something similar for PCI cards but unfortunately not for PCIe.

---

