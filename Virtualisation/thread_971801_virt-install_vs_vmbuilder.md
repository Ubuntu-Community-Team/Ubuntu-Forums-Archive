---
title: "virt-install vs vmbuilder"
date: 2008-11-05
forum: Virtualisation
---

### Post by stephanhughson on 2008-11-05
Hi,

I'm not sure if I 100% understand the difference between virt-install and vmbuilder.

Am I right in saying that...

* virt-install lets you install any OS from an ISO image?

* vmbuilder lets you install certain OS's only, over the Internet.

* when installing from an ISO it's not as optimised?

Should I be using vmbuilder whenever possible, unless I want to install something like Windows, and then be using virt-install in that case only?

Or is virt-install the new way of doing things?


Thanks for your time.

---

### Post by pred2k on 2008-11-05
i want to know that too.

And what are the advantages of virt-install compared with the simple kvm-command.

---

### Post by rmcewen on 2008-11-05
1. I believe you are correct in that vmbuilder is specifically geared toward creating guests of stripped down versions of Linux distributions whereas virt-install is the more generic option.

I think the kernel and packages of the guest distros that vmbuilder creates have a lot of the drivers, etc. removed since they would not be needed as the vm only supports a limited set of devices on the guest, i.e. three network cards.

2. The difference between using virt-install and the native kvm/qemu commands is that virt-install is part of the libvirt management package and will create the xml config files in /etc/libvirt needed to use libvirt and associated tools (virsh, virt-manager, etc).  If you want to use these tools at any point, it's easier to create the vm's with virt-install, otherwise you have to manually create the config files and "import" ('define' in libvirtspeak) them.

---

