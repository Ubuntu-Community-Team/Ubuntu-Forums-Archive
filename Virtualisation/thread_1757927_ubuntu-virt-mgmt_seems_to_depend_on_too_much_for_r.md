---
title: "ubuntu-virt-mgmt seems to depend on too much for remote"
date: 2011-05-14
forum: Virtualisation
---

### Post by jlanawalt on 2011-05-14
I am checking out KVM virtualization on Ubuntu using a 11.4 desktop system as the server and an 11.4 laptop as the management workstation and following the [community KVM installation guide]("https://help.ubuntu.com/community/KVM/Installation").

When I got to the step where I install the remote management software on the laptop it says to use ubuntu-virt-mgmt which "installs what you need to administer [your kvm instances] from a management station".

When I selected it for install, python-vm-builder is pulled in with a depends requirement and it pulls in debootstrap, qemu-common, qemu-kvm, seabios, and vgabios all as dependencies *on my management* system. This seems excessive for remote management.

To be fair, the ubuntu-virt-mgmt package description says it's a meta package to pull in common packages for creating, deleting and managing virtual machines...either on a local system *or [remotely]*.

The virt-manager package pulls in much less as depends. Is it a more appropriate package for remote management?

Am I awake in the night thinking I shouldn't need all that extra stuff on my remote management system?

Even for local on the server it seems that the above mentioned tools are required on the server not the remote management console.

---

