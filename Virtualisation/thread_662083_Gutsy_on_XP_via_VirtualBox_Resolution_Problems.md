---
title: "Gutsy on XP via VirtualBox: Resolution Problems"
date: 2008-01-08
forum: Virtualisation
---

### Post by jjsonp on 2008-01-08
I've recently installed VirtualBox on two different XP machines, then a VirtualMachine with Gutsy on each.

Both have the same problem: maximum resolution of 1024 x 768.

I've googled and searched the forums and tried about a dozen different ways: adding desired resolution to xorg.conf manually (as described in the VirtualBox manual), changing the mouse driver to "vboxmouse", running sudo dpkg-reconfigure -phigh xserver-xorg and following the prompts, etc. I've also installed the Guest Additions, both separately and in conjunction with manually modding xorg.conf.

Other than totally screwing up my display and having to recover from safe mode, I've had no luck at all. Max res will never go over 1024 x 768. 

From what my searching has turned up this is a fairly common problem, but I've tried the solutions offered, so either I'm missing something or I'm stuck at that resolution for the current version of VirtualBox at least. Any ideas or help most appreciated!

---

