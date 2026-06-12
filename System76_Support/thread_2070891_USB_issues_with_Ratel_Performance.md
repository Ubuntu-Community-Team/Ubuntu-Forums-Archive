---
title: "USB issues with Ratel Performance"
date: 2012-10-14
forum: System76 Support
---

### Post by jpfle on 2012-10-14
Hi,

On my new Ratel Performance, I have 2 USB issues:

[LIST]My USB keyboard is recognized by the BIOS and by Grub, but immediately after Grub loads the default menu option, the USB keyboard stops being recognized. When the LightDM menu appears, I must wait about 10 or 20 seconds for the keyboard to be usable again.[/LIST]

[LIST]My external USB-powered drive (Western Digital) is not mountable (it's just a ext4 partition). dmesg sees the drive when I connect it, but that's all. lsusb, fdisk, GParted, SpaceFM, Thunar, Nautilus, etc. don't see it, so I can't mount it.

I can use this drive with my netbook, so I don't think the problem is with the drive itself.

I tested several USB ports, USB 2, USB 3, but the problem remains.[/LIST]

My kernel: Linux ordi 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Any idea?

Thanks a lot.

---

### Post by isantop on 2012-10-15
> **jpfle said:**
> Hi,

On my new Ratel Performance, I have 2 USB issues:

[LIST]My USB keyboard is recognized by the BIOS and by Grub, but immediately after Grub loads the default menu option, the USB keyboard stops being recognized. When the LightDM menu appears, I must wait about 10 or 20 seconds for the keyboard to be usable again.[/LIST]

[LIST]My external USB-powered drive (Western Digital) is not mountable (it's just a ext4 partition). dmesg sees the drive when I connect it, but that's all. lsusb, fdisk, GParted, SpaceFM, Thunar, Nautilus, etc. don't see it, so I can't mount it.

I can use this drive with my netbook, so I don't think the problem is with the drive itself.

I tested several USB ports, USB 2, USB 3, but the problem remains.[/LIST]

My kernel: Linux ordi 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Any idea?

Thanks a lot.

Can you try with a stock Ubuntu kernel? We don't do testing with alternate kernels, and that's my guess about what's causing your issues.

---

### Post by jpfle on 2012-10-15
> **isantop said:**
> Can you try with a stock Ubuntu kernel? We don't do testing with alternate kernels, and that's my guess about what's causing your issues.

Indeed, I don't use a custom compiled kernel. Kernel 3.5.0-17 is the default kernel in the next version 12.10 that will be in final release in 3 days.

But I have the same problems if I choose the kernel 3.2.0-31 in the grub menu:

Linux ordi 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jbelmonte on 2012-10-16
Does the same thing happen when you boot from a live CD?

---

### Post by isantop on 2012-10-17
> **jbelmonte said:**
> Does the same thing happen when you boot from a live CD?

Agreed. I'm not seeing this on our Ratel here in the shop. Are you having issue with other USB devices, or just these two?

---

### Post by jpfle on 2012-11-11
> **jbelmonte said:**
> Does the same thing happen when you boot from a live CD?

[LIST]With a live Ubuntu 12.04: the external drive is not recognized at startup, but if I disconnect it and reconnect it in the USB port, it's mounted.[/LIST]

[LIST]With a live Ubuntu 12.10: the external drive is not recognized at startup, and if I disconnect it and reconnect it in the USB port, it's not recognized either.[/LIST]

---

### Post by isantop on 2012-11-12
> **jpfle said:**
> [LIST]With a live Ubuntu 12.04: the external drive is not recognized at startup, but if I disconnect it and reconnect it in the USB port, it's mounted.[/LIST]

[LIST]With a live Ubuntu 12.10: the external drive is not recognized at startup, and if I disconnect it and reconnect it in the USB port, it's not recognized either.[/LIST]

It's normal for external drives not to be recognized at boot. Are you still seeing problems with your keyboard on the live disk?

---

### Post by jpfle on 2012-11-12
Sorry, I have perhaps not been sufficiently explicit. By "startup", I mean when the desktop environment is fully loaded.

I've done a few tests. The external drive is already connected in a USB port when I boot on the live CD:

- With a live Ubuntu 12.04: the external drive is sometimes recognized when Unity is fully loaded (I see its icon on the Unity dash), but sometimes not. However, if I disconnect it and reconnect it in the USB port, it's always recognized.

- With a live Ubuntu 12.10: the external drive is never recognized, neither when Unity is fully loaded, nor if I disconnect it and reconnect it in the USB port. Therefore, the external drive is unusable.

About the USB keyboard:

- With a live Ubuntu 12.04: the keyboard is always recognized when I see the live menu. I choose "Try Ubuntu without installing", then sometimes the keyboard is still recognized (so I can toggle with arrows between the graphical boot process or the textual boot process), sometimes it stops working for about 20 seconds, until the desktop environment begins to load.

- With a live Ubuntu 12.10: the keyboard is always recognized.

---

