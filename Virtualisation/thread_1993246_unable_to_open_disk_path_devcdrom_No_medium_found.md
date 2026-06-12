---
title: "unable to open disk path /dev/cdrom: No medium found"
date: 2012-06-01
forum: Virtualisation
---

### Post by piriton on 2012-06-01
I am trying to add a new virtual machine using KVM.  I am almost there, but this is preventing me from creating the KVM guest.


```

root@ubuntu:~# kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used

root@ubuntu:~# virt-install --name virt1 -r 512 --disk path=/var/lib/libvirt/images/virt1.img,size=20 --cdrom /dev/cdrom --accelerate --connect=qemu:///system --vnc --noautoconsole -v

Starting install...
ERROR    unable to open disk path /dev/cdrom: No medium found
Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start virt1
otherwise, please restart your installation.

root@ubuntu:~# ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 Jun  1 23:55 /dev/cdrom -> sr0

```

---

### Post by piriton on 2012-06-03
virt-install was simply looking for the installation media.

I would suggest pointing to an .iso file instead which is easier.  see virt-install manpage for instructions.

---

