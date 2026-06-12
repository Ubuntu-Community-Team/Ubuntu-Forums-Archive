---
title: "installing VMware tools and extending the screen in VNC"
date: 2010-12-27
forum: Virtualisation
---

### Post by Cr0n_J0b on 2010-12-27
Hey everyone.

I have a recently loaded VMware guest Ubuntu 10.10 on my ESXi 4.1 host.  I would like to have the ability to extend the resolution of the VNC session to cover both of my monitors.  In the old physical machine, I just went into the nVidia tools and there was a setting for it...I think it was overscan or something.  I just set it and boom...done.  In the guest version doesn't have this option.  Is there a way to set this up properly?

Again, I'm not looking to change the desktop resolution of the guest, so much as the resolution that the VNC client sees.  I would like it to be something around 3600 x 1050.

also, maybe related...how can I make sure that VMware tools is properly loaded?  I followed the steps in the ubuntu community guide, but I just want to be sure.

thanks

---

### Post by Cr0n_J0b on 2010-12-30
bump

---

### Post by dcstar on 2010-12-31
> **Cr0n_J0b said:**
> 
.......
Again, **I'm not looking to change the desktop resolution of the guest**, so much as the resolution that the VNC client sees.  I would like it to be something around 3600 x 1050.
.......

That is **exactly** what VNC uses.

---

