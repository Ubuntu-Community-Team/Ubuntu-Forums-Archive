---
title: "Virtualbox 3.2 in terminal"
date: 2010-11-01
forum: Virtualisation
---

### Post by cloud2dream on 2010-11-01
Hi

I've got virtualbox 3.2 (the non-ose version) on karmic 32bit desktop, and I want to run it from the command line with gdm stopped. The problem is I can't find any commands for it, they all relate to the OSE version, which isn't as good.

If anyone has any help with this it would be greatly appreciated. Ideally I just want to be able to start a VM from the command line (ctrl+alt+f1) after doing gdm-stop.

Thanks
James

---

### Post by CharlesA on 2010-11-02
The commands are the same for OSE and non-free version.

If you are wanting to start a VM without a GUI, run VBoxHeadless -s **VMNAME** -p **VRPDPORT**

---

