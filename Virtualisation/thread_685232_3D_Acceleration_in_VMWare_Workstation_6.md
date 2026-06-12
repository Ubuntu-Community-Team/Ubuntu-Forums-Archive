---
title: "3D Acceleration in VMWare Workstation 6"
date: 2008-02-02
forum: Virtualisation
---

### Post by TP100 on 2008-02-02
I've been searching for an answer to this, but I haven't seen anything specifically relating to my question.

Currently running Windows Vista on AMD64 X2 with VMWare Workstation 6.  I'm looking to run Ubuntu as a guest OS on my Vista host.  My goal is to get some sort of 3D acceleration so I can play around with the 3D tools in Ubuntu as well as some of the add-on eye candy stuff like Compiz.

Does anyone have infomration on how this is possible?  It sounds like Workstation 6.0 does have some experimental 3D accleration stuff built-in, so I'm hoping to utilize some of it.

Thanks.

---

### Post by Shazaam on 2008-02-02
Desktop effects like compiz won't work correctly (or at all) with virtualization. VMware hard codes an SVGA2 video card in their product that at the moment you cannot change.

---

### Post by TP100 on 2008-02-02
> **Shazaam said:**
> Desktop effects like compiz won't work correctly (or at all) with virtualization. VMware hard codes an SVGA2 video card in their product that at the moment you cannot change.

Well crap... I guess I should just take the plunge :)

Thanks for the quick response.

---

### Post by OmegaBLK on 2008-02-02
> **TP100 said:**
> 
It sounds like Workstation 6.0 does have some experimental 3D accleration stuff built-in, so I'm hoping to utilize some of it.


It does have experimental Direct3D support, but only Windows 2000 and Windows XP guests are supported.

---

