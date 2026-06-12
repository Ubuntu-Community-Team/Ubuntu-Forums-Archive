---
title: "Cannot install Windows XP Pro x64 in QEMU KVM"
date: 2009-11-17
forum: Virtualisation
---

### Post by EndingPop on 2009-11-17
I've been trying to install Windows XP x64 in a VM under Ubuntu Karmic Koala (9.10) x86-64 mostly using the instructions from the link below:

[http://ubuntuforums.org/showthread.php?t=1293199](http://ubuntuforums.org/showthread.php?t=1293199)

So it loads the image and boots from CD. When it gets to the screen in the Windows installer that says "Setup is starting Windows" it just sits there maxing out the processor usage. A couple of times I got BSODs, but I haven't been able to reproduce it so I'm not sure why they happened or why they seem to have stopped happening.

The processor is an Intel Core 2 Duo T9600 (which supports Intel-VT).

Any help is appreciated.

---

### Post by EndingPop on 2009-11-20
Help?

---

### Post by devvy on 2009-11-23
I have the same problem. Under Windows 7 with QEMU 0.9.0 I got it working, but not with the later snapshots of Qemu -- also not under Ubuntu.

---

