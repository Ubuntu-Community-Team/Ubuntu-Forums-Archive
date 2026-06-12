---
title: "LibvirtQemu"
date: 2021-12-20
forum: Security
---

### Post by claudioreddi on 2021-12-20
Help me, please.
I'm on LTS16.04 in an HP laptop.
From about six months I get an opening splash-screen "LibvirtQemu" ask me pw for logging my computer.
My known pw doesn't work anymore so I by passed these logging like Host.
Whwn I try to update software in Ubuntu Center I'm prompt with pw and again my working old pw doesn't work.
The only effective way is from Terminale in su mode and hera my old pw is accepted and I can go further with uptdate and so on.
Someone could help me to solve this problem? What is LibvirtQemu? Wy my pw doesn't work anymore in UbuntuSoftwareCenter and when I try any update and is unchanged in su-mode and only in terminal way I can do that update or upgrade?
Thanks to everibody for reading me.
Carlo

---

### Post by deadflowr on 2021-12-20
LibvirtQemu is a system user specifically used by the libvirtd service,
which in turn is a service to control/manage virtual machines, usually of the kvm variety.
It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1674765]("https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1674765")
See this thread for how to set it not to show: [https://askubuntu.com/questions/897026/why-do-i-have-a-libvirt-qemu-account-in-lock-switch-account-options-in-ubuntu/940069#940069]("https://askubuntu.com/questions/897026/why-do-i-have-a-libvirt-qemu-account-in-lock-switch-account-options-in-ubuntu/940069#940069")

In terms of your password issue I don't know what's going on with that.
I would assume when logging in you should see other user names listed to choose from beside libvirtqemu.
You can try scrolling up and down to select another.

---

### Post by claudioreddi on 2021-12-21
Many thanks. I'll work on that,
Ciao

---

### Post by TheFu on 2021-12-21
LTS16.04 support ended for most GUI flavors almost 3 yrs ago.  For KDE and Gnome3 desktops or a real server install, supported ended last April.

This is a problem because all the 16.04 repos have been moved/hidden since that point and only systems setup for ESM support from Canonical have been getting patched.

At this point, upgrades are probably more trouble than they are worth for most users.  Download 20.04 and do a fresh install.  Obviously, backup whatever data and settings you cannot lose first.

A 5 yr old computer may not run the default Ubuntu 20.04 with Gnome3 DE so well. It needs more RAM, CPU, and a better GPU than 16.04 did. If you'd like advice for a desktop flavor to install, please provide specific details about the RAM, CPU and GPU.  **inxi -mbz** output would be fine.  On some flavors, *system information *is preinstalled as a tool in the menu. I don't recall whether 16.04 had it or not. Sorry.

A fresh 20.04 install solves the issues above, so dealing with them isn't really all that important.  You can run the 20.04 in a "Try Ubuntu" mode, booted from a flash drive, and use that to copy off all the data you don't want to lose before doing a fresh install to the HDD/SSD of the system.

---

