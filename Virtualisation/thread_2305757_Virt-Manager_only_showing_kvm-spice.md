---
title: "Virt-Manager only showing kvm-spice"
date: 2015-12-08
forum: Virtualisation
---

### Post by zexelon2 on 2015-12-08
I am having a bit of an issue with Virt-Manager on Ubuntu 15.10. When I connect to the qemu connection and create a VM under the Overview tab under Hypervisor Details it shows:

Hypervixor kvm
Achitecture: x86_64
Emulator: /usr/bin/kvm-spice
Firmware: Default

All these options are grayed out and I can not change them. I want to change from kvm-spice to the qemu emulator. I have qemu installed from the qemu-kvm package and have verified that I can run qemu from the command line. 

How do I get virt-manager to let me configure qemu?

EDIT: Further to this, when I check the localhost: Connection Details Overview tab it lists Hypervisor: qemu there...

---

### Post by deadflowr on 2015-12-10
It's done during the vm creation.
At the end of the setup you'll get to the last page marked 5 of 5
It'll have an line marked as Advanced options.
Toggle that line and it'll give you the option to change the virt type the arch type and the firmware.

---

### Post by KillerKelvUK on 2015-12-17
So I'm running 15.04 with virt-manager v1.2.1...the Architecture option is selectable at the start so x86_64 vs. SPARC etc.  The firmware option is available at the end if you check the option to further configure the guest before first running it, this I think only present if you have installed OVMF and configured libvirt with knowledge of it.

Regards your actually stated requirement to change the Emulator to use qemu...well qemu IS used by KVM for guests...if you start a guest and issue 'ps aux | grep qemu' into the terminal if will return the qemu command line used to start the guest.  To my understanding you cannot us virt-manager to run a qemu only guest without KVM extensions loaded in the kernel.  If you want to use QEMU and only QEMU then you need a GUI like Aqemu i believe.

---

