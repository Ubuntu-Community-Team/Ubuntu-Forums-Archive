---
title: "Console graphics mode in 10.04 with ATi Rage XL"
date: 2010-07-26
forum: Server Platforms
---

### Post by cracker on 2010-07-26
I recently upgraded a system running Ubuntu Server 8.04 to 10.04. Previously, this system was set up to use 1024x768 resolution on the framebuffer, with a vga=0x318 parameter. However, after the upgrade, all I got was an "Out of range" error on my monitor. I tried several other modes, but none worked except the default resolution. I couldn't find any information on using grub 1 with lucid, so I upgraded to grub2, which went smoothly, but now it won't go into any higher resolutions when I set them in /etc/default/grub and run update-grub2. I ran vbeinfo at the grub console, and it shows that the card supports everything up to 1280x1024 32-bit color, and it used to work before the upgrade. What happened? How can I fix it?

---

### Post by Vegan on 2010-07-26
Try over in the desktop crowd, we use no GUI over here.

:guitar::guitar:

---

### Post by cracker on 2010-07-26
I'm not using a GUI, this is not X. It is the console framebuffer.

---

### Post by cracker on 2010-07-27
I got it working with some help from the IRC channel. Here's what I had to do:

In [font="Courier New"] /etc/initramfs-tools/modules [/font] add ```
radeonfb
```

In [font="Courier New"] /etc/grub.d/00_header [/font] add ```
set gfxpayload=keep
``` just below ```
set gfxmode=${GRUB_GFXMODE}
```

In [font="Courier New"] /etc/default/grub [/font], set ```
GRUB_GFXMODE=1024x768x24
```

Run ```
sudo update-initramfs -u && sudo update-grub && sudo reboot
```

---

### Post by MeduZa on 2012-12-22
works for me too :)

---

### Post by cariboo on 2012-12-24
This is a 2 year old thread, and as such needs to be closed. Thread Closed.

---

