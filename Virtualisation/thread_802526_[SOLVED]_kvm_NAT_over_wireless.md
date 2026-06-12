---
title: "[SOLVED] kvm NAT over wireless"
date: 2008-05-21
forum: Virtualisation
---

### Post by igwk on 2008-05-21
I'm running a winxp virtual machine using KVM on Hardy with the following command:

[FONT="Courier New"]kvm -hda ~/vm/winxp_vm.qcow2 -cdrom /dev/cdrom -m 768 -soundhw es1370 -no-frame -no-acpi &[/FONT]

By default it's using the qemu user mode network stack for network access and this works fine when my host machine is connected to the network with eth0.  However, there are times when my host machine is connected to the network over wireless (wlan0) instead.  Does anyone know how to make kvm use the user mode guest networking over wlan0 instead of eth0?  Do I need to setup TAP interfaces and switch to NAT to make this work?

---

### Post by igwk on 2008-05-22
Looks like the problems I had before occurred when I had both wired and wireless enabled at the same time, turned off the wired network, and didn't properly disable the interface.  If I only connect to the network with wireless and start kvm with the user mode network stack everything works just fine!

---

