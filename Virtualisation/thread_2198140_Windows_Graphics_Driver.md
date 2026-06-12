---
title: "Windows Graphics Driver"
date: 2014-01-07
forum: Virtualisation
---

### Post by woopud on 2014-01-07
So, I finally dumped Windows 8 after loosing GRUB for the 8th time....  I wiped my hard drive and installed Ubuntu 13.10 as the sole OS, after that I installed Virtual Box and Windows 7 inside of that.  Everything works fine except I can't install the right graphics driver?

---

### Post by Kirboosy on 2014-01-07
How are you trying to install the graphics driver? Are you installing the "Guest Additions"?

Its located under "Devices" --> "Guest Additions" (or Host + D)

~Caboose

---

### Post by QIII on 2014-01-07
If you have Windows installed in the VirtualBox VM, it is already running the correct driver.

Your VM does not have direct contact with your physical graphics card.  Instead, the machine is running on a hardware abstraction layer on "hardware" provided by VirtualBox.  The "graphics card" is a custom VESA compliant abstraction, not your physical GPU.  Virtualbox uses a software communication channel between the abstracted GPU and your physical GPU.  This is one of the reasons that video performance is so abysmal in VirtualBox.

To get good graphics, you would have to use a virtualization solution like KVM(Kernel-based Virtual Machine) with Spice or the like to directly interface with the physical hardware.

---

