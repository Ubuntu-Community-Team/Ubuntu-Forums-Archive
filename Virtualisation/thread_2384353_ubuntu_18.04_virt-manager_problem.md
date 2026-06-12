---
title: "ubuntu 18.04 virt-manager problem"
date: 2018-02-06
forum: Virtualisation
---

### Post by luki3who on 2018-02-06
hi
last day i upgrade to xubuntu 18.04. in virt-manager i have error when use build dipslay 
** QEMU &#8222;getfd&#8221;: No file descriptor supplied via SCM_RIGHTS.**
when use virt-viwer **virt-viewer qemu:///system** i see virtual machine.

i started used virt-manager i can do somethink wrong.

i try:```

sudo apt purge libvirt-bin libvirt-glib libvirt0 virt-manager virt-viewer virtinst 
sudo apt purge libvirt-bin libvirt-glib-1.0-0 libvirt0 virt-manager virt-viewer virtinst 
sudo apt install libvirt-bin libvirt-glib libvirt0 virt-manager virt-viewer virtinst 
sudo apt install libvirt-bin libvirt-glib-1.0-1 libvirt0 virt-manager virt-viewer virtinst 
sudo apt install libvirt-bin libvirt-glib-1.0-0 libvirt0 virt-manager virt-viewer virt

virt-manager --version 1.4.0
virt-viewer --version virt-viewer w wersji 6.0
 libvirtd --version libvirtd (libvirt) 4.0.0
```

---

### Post by TheFu on 2018-02-06
Welcome to the forums.

18.04 is alpha. Not yet released.
The only "trick" I remember using libvirtd on 14.04 and 16.04 is to ensure the userid is part of the libvirtd group.

---

### Post by ajgreeny on 2018-02-06
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by Doug S on 2018-02-06
See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1747442").

---

