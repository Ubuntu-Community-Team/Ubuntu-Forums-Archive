---
title: "Ubuntu Server 20.04 guest stuck at &quot;Booting from hard disk&quot;"
date: 2020-07-03
forum: Virtualisation
---

### Post by uc50_ic4more on 2020-07-03
Hello -

I have a 20.04 desktop and have installed gnome-boxes (and added myself to the kvm group). After running through the Ubuntu Server 20.04 installation process and rebooting I am stuck at "Booting from hard disk". My guess, of course, is that this is a UEFI issue but I am unsure how to correct it. I would appreciate any help.

---

### Post by oldfred on 2020-07-03
Do you now have two Ubuntu installs? One desktop & one server?
Are both installs UEFI? 
You only get one boot & grub menu that then would offer to boot other install.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by uc50_ic4more on 2020-07-03
> **oldfred said:**
> Do you now have two Ubuntu installs? One desktop & one server?


I have a 20.04 Desktop installed (UEFI) on a spare machine. I am attempting to install Server 20.04 as a gnome-boxes VM via gnome-boxes' suspiciously-sparse GUI install process. Using the virt-manager GUI VM installer everything went well; so I suppose I am just curious about what I am missing with gnome-boxes.

---

