---
title: "kvm vs. qemu-system-x86_64 no compatibillity?"
date: 2009-02-17
forum: Virtualisation
---

### Post by Tasu on 2009-02-17
Hi,
I need to clear some myst around an issue I'm having...

I installed a sme server 7.4 (a centos based distro) in a virtual host system based on ubuntu Intrepid 8.10, I followed the instructions in [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM), the installation went ok, the system runs.
I dumped the config in a xml file, and found that the program used to run the guest is qemu-system-x86_64.. I was expecting kvm. I controlled on another network where I have the same (even hardware for the host) configuration, that network is running a 8.04 host not 8.10 like the new one, but was thinking about upgrading even the old one since the bridge interface in 8.10 has less glitches, the xml config in the old host stated that teh used program is kvm.
My paranoia started to make me think about a performace issue (but, I don't know how to test it), since a boot time filesystem check took really too long time on the new system, then I thought.. probably the qemu-system-x86_64 don't use hardware acceleration of my xeon quad core, I must use kvm like in the old system.
Folowing this thought, I destroyed and undefined the guest, changed in the xml file qemu-system-x86_64 with kvm (and qemu with kvm) and defined and started the system again... suddenly, I wasn't able to ping it and watch it via vnc anymore...
I've always thought that kvm and qemu-system-x86_64 are similar, that I can switch between them easily, and I always thought kvm is faster (guests are faster) than qemu-system-x86_64, do my two guessings are erroneous? Why can't I use KVM in the new system? Are guests ran by qemu-system-x86_64 slower (not using VTx extensions, for example) than KVM one?

Thank you for the answers
G.

---

