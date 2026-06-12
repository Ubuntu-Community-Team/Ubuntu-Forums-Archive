---
title: "KVM could not open root.qcow2"
date: 2010-11-18
forum: Virtualisation
---

### Post by Dreetnp on 2010-11-18
I've tried to get KVM running on ubuntu.
I followed the [tutorial]("https://help.ubuntu.com/community/KVM") from the ubuntu website.
Everything went well until I tried to create the qcow2 image and then move the VM to the block device with the qemu-img.

/dev/sda4 is mounted on /kvm, on /kvm I created 5 folders (guest1 - 5). 
Commandline:
$ sudo qemu-img convert root.qcow2 -O raw /kvm/guest1

I get the error message:

qemu-img: Could not open 'root.qcow2'


Does anyone know what I'm doing wrong?


Thanks,


Dreetnp

---

