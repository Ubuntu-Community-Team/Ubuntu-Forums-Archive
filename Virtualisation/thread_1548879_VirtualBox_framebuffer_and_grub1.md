---
title: "VirtualBox framebuffer and grub1"
date: 2010-08-09
forum: Virtualisation
---

### Post by bsanyi on 2010-08-09
Hi,

I'm using an Ubuntu based linux in VirtualBox, and
have a small problem with the framebuffer console.
I need to enforce the video mode into 800x600, and
with grub2 + gfxmode + gfxpayload this works fine.
My problem is that I need to achive the same effect
in grub1.   I've tried lots of vga=xxx codes, but almost
all of them makes my console unusable.  Can you
please tell me what kernel paramethers should I pass
in with grub1 to make this work?  (What is the same
in my menu.lst than "set gfxmode=800x600" and
"set gfxpayload=800x600" in grub2?)

Guest kernel:  2.6.23-32-generic, Ubuntu
VirtualBox: 3.2.6

THX,
s.

---

### Post by -Duvel- on 2010-08-11
Hi,

I have the same problem with vmware.
The console turns black if I append a vga= cmdline parameter.

---

