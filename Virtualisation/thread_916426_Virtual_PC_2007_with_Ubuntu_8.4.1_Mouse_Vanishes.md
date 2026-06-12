---
title: "Virtual PC 2007 with Ubuntu 8.4.1: Mouse Vanishes"
date: 2008-09-10
forum: Virtualisation
---

### Post by Zian on 2008-09-10
Situation:
Windows Vista running Virtual PC 2007
Ubuntu 8.4.1 running inside Virtual PC

I've searched through the documentation, these forums, and other places and I can't find a solution for my mouse problem.

The mouse completely vanishes after I log into Ubuntu. When I use the context-menu key on my keyboard, the trash context menu appears, which suggests that the mouse cursor is somewhere in that direction. However, no matter how I wiggle the mouse, the cursor never reappears.

I've already set vga=791 noreplace-paravirt i8042.noloop in GRUB. I've also checked to make sure xorg.conf shows "mouse" instead of "vmmouse".

Any ideas that you can provide will be greatly appreciated.

(P.S. I'm back to using VPC instead of VirtualBox because VPC will start instead of VirtualBox, which just sits around eating CPUs forever. I'd switch back to VirtualBox in an instant if it actually...ran.)

---

