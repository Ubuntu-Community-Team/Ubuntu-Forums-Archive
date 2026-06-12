---
title: "GRUB: specify video card to be used"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jvolkman on 2012-03-24
I have a Core-i5 system with integrated graphics as well as an additional Nvidia card. I use the Nvidia card for X, which works fine, and I'd like to use it for the virtual consoles and GRUB as well. However, both GRUB and the virtual consoles use the integrated graphics device.  When I switch from X to a virtual console (ctrl+alt+f1, for example), the Nvidia display just goes black.

Is there a way to specify which device GRUB and the consoles use?

Thanks.

---

### Post by xebian on 2012-03-24
> **jvolkman said:**
> I have a Core-i5 system with integrated graphics as well as an additional Nvidia card. I use the Nvidia card for X, which works fine, and I'd like to use it for the virtual consoles and GRUB as well. However, both GRUB and the virtual consoles use the integrated graphics device.  When I switch from X to a virtual console (ctrl+alt+f1, for example), the Nvidia display just goes black.

Is there a way to specify which device GRUB and the consoles use?

Thanks.

Not exactly an expert here but IIRC, you need to disable the on-board graphics in your BIOS when you add an external graphics card.  At least that's what mine is- either or not both at the same time.

---

### Post by jvolkman on 2012-03-24
I can definitely disable the integrated device which solves the issue.  If possible, I'd like to leave it enabled so I can play around with Wayland (essentially letting Wayland use the Intel device while X uses the Nvidia device).

---

