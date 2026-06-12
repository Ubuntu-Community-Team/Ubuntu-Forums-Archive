---
title: "Ubuntu + Virtualize + Graphics"
date: 2008-11-29
forum: Virtualisation
---

### Post by HenkR on 2008-11-29
Hi,

Is it possible to install Ubuntu on a virtual pc (virtual pc, vmware, virtualbox, ...) AND also get the nice graphic effects and the cube?
I installed Ubuntu on Virtualbox but it doesn't recognize my Nvidia Geforce 8800 GTS.

---

### Post by HotShotDJ on 2008-11-29
> **HenkR said:**
> Is it possible to install Ubuntu on a virtual pc (virtual pc, vmware, virtualbox, ...) AND also get the nice graphic effects and the cube?As far as I am aware, only VMWare has 3D graphic support for a guest OS, which is what Compiz (the Cube and other effects) require.  However, it is important that you are aware that 3D support is still pretty buggy.  You may be better off using a dual-boot set up.  Or, possibly set things up so that Ubuntu is the host OS with Windows as the guest (although you'll run into the same issue if you want 3D, such as DirectX, to run in Windows).

---

### Post by HenkR on 2008-11-30
OK

I have a pc with windows and one HD. Can I use dual boot if I get a new HD and install Linux on the new HD?

Or do I need to install it on my current HD to use dual boot?

---

### Post by HotShotDJ on 2008-11-30
> **HenkR said:**
> I have a pc with windows and one HD. Can I use dual boot if I get a new HD and install Linux on the new HD?Yes.  If you get a second hard drive, you certainly can install Linux on it.  You could also have the Ubuntu installer shrink your Windows partition and then install itself on the drive you already have.  Its completely up to you.

---

### Post by HenkR on 2008-11-30
And do I also need something else for making the dual boot possible or does the bios automatically recognizes the two operating systems on the two HD's?

---

### Post by HotShotDJ on 2008-11-30
> **HenkR said:**
> And do I also need something else for making the dual boot possible or does the bios automatically recognizes the two operating systems on the two HD's?Its not the bios that performs the "magic" of dual booting.  The Ubuntu installation process includes installing a boot loader where the BIOS will automatically see it.  This software will run when you first boot up, and then transfer control to whichever operating system you want to boot up via a very simple menu.

The Ubuntu installer handles it all for you.  You won't have to make any BIOS changes.

---

