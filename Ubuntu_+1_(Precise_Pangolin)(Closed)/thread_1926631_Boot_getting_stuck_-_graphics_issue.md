---
title: "Boot getting stuck - graphics issue?"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Irihapeti on 2012-02-16
I have an install of precise with Openbox on my Asus EeePC 900. Around about kernel version 3.2.0-9, it started getting stuck about half-way through booting. Originally it was at "checking battery state", but more recently I've seen references to mounting.

It's not a complete freeze, because I can use alt-f2 to get a tty, then login and run "startx", and everything works normally from then on.

I've come across this problem elsewhere, but it seems to mainly be related to nVidia graphics. This machine has Intel i915 graphics, and I've not seen any reference to any fix for this chip.

To add to the confusion, I have another install on the same machine with a standard Gnome fallback desktop, and I don't have this problem.

Does anyone have any ideas?

---

### Post by dino99 on 2012-02-16
nowadays the kernel directly deals with X, so no need of xorg.conf (except special needs)
then using  tool to create one is a bad idea. Dont know exactly how is the situation with i915 chipset but googling around might help (some times ago nomodeset was used on the boot line)

---

### Post by Irihapeti on 2012-02-16
I know about xorg.conf being obsolete except in special cases. However, your comment caused me to go looking for an "xorg.conf.failsafe" file, and, sure enough, there's one there AND it's regenerated on reboot if I remove it.

Now to find out why it's doing that...

---

### Post by Irihapeti on 2012-02-18
Update:

It wasn't a graphics issue after all. It turned out to be a bug in lightdm, which I was using instead of lxdm.

I removed lightdm and installed lxdm instead and everything works properly. I've reported a bug against lightdm.

So I think I can mark this solved.

---

