---
title: "surviving virtual machine at host reboot"
date: 2010-08-10
forum: Virtualisation
---

### Post by tapas_mishra on 2010-08-10
I am using KVM and Ubuntu.
I have some virtual machines running on it.

Is there a way I can do some thing so that the virtual machines always restart when I reboot the host operating system.
In xen I used to have a symlink 
in /etc/xen/auto to the vm in question.

---

### Post by sh1ny on 2010-08-10
If you're using libvirt ( and you should be ), you have to 2 options :

1. Symlink : ln -s /etc/libvirt/qemu/machine.xml /etc/libvirt/qemu/autostart/machine.xml


2. Use virt-manager and in "Boot Options" section check the "Start virtual machine on host boot up" option.

---

### Post by tapas_mishra on 2010-08-10
> **sh1ny said:**
> If you're using libvirt ( and you should be ), you have to 2 options :

1. Symlink : ln -s /etc/libvirt/qemu/machine.xml /etc/libvirt/qemu/autostart/machine.xml


Well I did not had autostart in ```
/etc/libvirt/qemu
```
> **sh1ny said:**
> 
2. Use virt-manager and in "Boot Options" section check the "Start virtual machine on host boot up" option.

Good idea but tell about the first one I want to try it.

---

### Post by sh1ny on 2010-08-10
Create it then.

mkdir -p /etc/libvirt/qemu/autostart

:)

---

### Post by tapas_mishra on 2010-08-10
Ah !!
I thought I am not supposed to create it :)

Both the methods work fine.
Thanks.

---

