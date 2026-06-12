---
title: "vmware stationwork 7"
date: 2010-03-12
forum: Virtualisation
---

### Post by davarse on 2010-03-12
im a newbie in linux and i need some help. i download trial version of vmware workstation 7 (VMware-Workstation-Full-7.0.1-227600.x86_64.bundle) from the webside for linux 64bit but i dont know how to install it. as i say i dont really understand linux, so i need to very clear guidance for the installation.
thank you

---

### Post by cariboo on 2010-03-14
A bump for the move.

---

### Post by freecode99 on 2010-03-21
Installing the VMware Workstation bundle is fairly straightforward:

1) Go to the directory where you downloaded the VMware*.bundle file then type:
[B]
chmod +x VMware-Workstation-Full-7.0.1-227600.x86_64.bundle[/B]

2) when the prompt returns, type:

**sudo ./VMware-Workstation-Full-7.0.1-227600.x86_64.bundle**

3) Next, follow the prompts in the GUI installer
4) Then use the Workstation as you normally would.

I'm a bit disappointed at the moment as the recent kernel update (2.6.31.20) seems to have broken VMware Workstation VMs. Virtual Box is working though. Wonder what broke exactly?

Good luck with installation, it isn't that hard, and will be recompiled every time you use it again after every kernel update. Except the last one apparently...

freecode

---

### Post by meskes on 2010-04-28
The only thing I was able to come up with was that it was a kernel/DKMS issue. .32 kernels on the host work just fine though so you may want to consider upgrading to lucid. Been on it since it was prealpha and it's been pretty solid.

---

### Post by fjgaude on 2010-04-29
Yes, Ubuntu 10.04 works great and Player 3.0.1 has kept up with each kernel upgrade without issues.

---

