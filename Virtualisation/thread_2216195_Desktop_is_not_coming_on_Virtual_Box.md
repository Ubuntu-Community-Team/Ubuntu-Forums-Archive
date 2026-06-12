---
title: "Desktop is not coming on Virtual Box"
date: 2014-04-10
forum: Virtualisation
---

### Post by Crazy01 on 2014-04-10
Hi,
I installed the Ubunto server (ubuntu-13.10-server-amd64.iso) on VirtualBox. But whenever I am starting my Virtual Machine its staring the terminal not the Desktop (GUI based).
What suppose to do to bring the desktop on the start up of my machine?
Please help me as I am new on Linux.

Thanks

---

### Post by steeldriver on 2014-04-10
The Server iso doesn't include a GUI desktop - it is meant to be administered entirely via CLI

If you want a desktop, either install one of the desktop versions from its own iso (regular Ubuntu, or lighter versions like Xubuntu or Lubuntu) or add the equivalent desktop package to what you already installed (my preference would be the lxde-core package - a nice basic desktop without any extras).

---

