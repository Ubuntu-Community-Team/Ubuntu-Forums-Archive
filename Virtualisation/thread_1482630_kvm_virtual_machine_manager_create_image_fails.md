---
title: "kvm virtual machine manager create image fails"
date: 2010-05-13
forum: Virtualisation
---

### Post by unclecameron on 2010-05-13
Lucid server, I loaded up Gnome to experiment with virtual machine manager, it won't create an .img file automatically, so 2 questions:

1. /var/lib/libvirt/* is owned by root.root, should it be someone else?
2. I can manually create the image using:
```

qemu-img create some.server.com.img -f qcow 8G

```
is that the best command to use? After I create the image I have to chmod 777 (testing remember) some.server.com.img to get it to work, I'm sure that's not the right way to do it though. Also, am I missing a package that would solve me problem? Here's what I installed:
```

aptitude install kvm libvirt-bin ubuntu-vm-builder bridge-utils

```
amd64, 8 xeon cores, 12G ram, 9TB raid10 storage

---

### Post by kevpatts on 2010-05-14
I was able to get this running just doing:
```
sudo apt-get install ubuntu-virt-server ubuntu-virt-mgmt
```
then I changed the "Virtual Machine Manager" menu entry to run:
```
gksudo virt-manager
```
and I was able to create virtual machines.

---

### Post by unclecameron on 2010-05-14
did that but it didn't solve the problem, it seems virt-manager doesn't have permission to generate the .img for some reason.

---

