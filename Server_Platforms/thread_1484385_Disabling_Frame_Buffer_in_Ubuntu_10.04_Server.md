---
title: "Disabling Frame Buffer in Ubuntu 10.04 Server"
date: 2010-05-15
forum: Server Platforms
---

### Post by gmjs on 2010-05-15
Hello,

Does anyone know how to disable the frame buffer in Ubuntu 10.04 Server?

It doesn't seem to take any notice if you use nofb or fb=false as a kernel argument and the terminal text scroll slowing down compiling a lot when running in a VirtualBox virtual machine.

Many thanks,

Graham

---

### Post by aaronk38 on 2010-05-22
I was able to disable the framebuffer by adding a blacklist entry for my particular vga driver into /etc/modprobe.d/blacklist-framebuffer.conf.

Added "blacklist vga16fb" (without the quotes) to the end of the list of other framebuffer drivers already there. Worked like a charm, got the nice, fast, classic console back.

You can use dmesg to determine which driver, e.g. vga16fb, the framebuffer is loading. Should be towards the end of the output, right after a boot.

To keep things extra clean, I un-commented GRUB_TERMINAL=console in /etc/default/grub to prevent GRUB from starting a framebuffer, but it's not really necessary.

---

### Post by gmjs on 2010-05-22
Excellent, thank you very much!  I might be able to compile PHP now in less than half an hour!

Thanks,

Graham

---

### Post by pallinger on 2011-02-07
A nicer solution (for me) to disable framebuffer was to use the nomodeset kernel boot option.

Also, if you run your compiles in *screen*, then you need not watch all text to be drawn to the terminal. This is also useful if you use a slow ssh connection.

---

