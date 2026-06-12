---
title: "Virtualisation help"
date: 2011-01-28
forum: Virtualisation
---

### Post by fongwee on 2011-01-28
Hi,

I am a complete noob in computing but is willing to learn. Currently, I am trying to get setup up a NAS and use the same computer to run as a HTPC.

I understand that I can do it with virtualisation. Can someone please point me in the right direction to some books or websites? I will try to install Ubuntu server 10.10.

Thanks

---

### Post by Neocult on 2011-01-29
To get an easy virtualization on the **desktop** I would recommend you VirtualBox for the start. Its easy to use and have good desktop integration. 

If you want virtualization on a **remote** computer espacially to run server systems in a virtual machine, I recommend you to install KVM and libvirt (*qemu-kvm* and *libvirt-bin* package) with virt-manager as the management GUI.

But I don't think so that you really need a virtualization solution.

Maybe it is enough for you to install Ubuntu Desktop on the PC, configure a TV card, and share your hard disk storage via Samba to other computers in the network. If not you should post some more information about what you want from your computer.

---

