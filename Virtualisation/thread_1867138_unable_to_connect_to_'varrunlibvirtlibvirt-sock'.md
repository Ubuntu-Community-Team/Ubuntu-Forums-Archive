---
title: "unable to connect to '/var/run/libvirt/libvirt-sock'"
date: 2011-10-22
forum: Virtualisation
---

### Post by antonello1 on 2011-10-22
I followed the setup procedure in [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) but after the following command: 

$ virsh -c qemu:///system list

the system give me the following error:

error: unable to connect to '/var/run/libvirt/libvirt-sock', libvirtd may need to be started: File or directory does not exist

I have the same error with VirtManager.

Any suggestion?

The system is Laptop çenovo T60 with UBUNTU 11.10 (32bit)

---

### Post by Dedoimedo on 2011-10-23
Do you have the libvirt daemon running?
If you do /etc/init.d/libvirt (or libvirtd) status, what does it return?
Dedoimedo

---

### Post by antonello1 on 2011-10-23
(1) I check the file '/var/run/libvirt/libvirt-sock' and I have nor the dir "libvirt".

(2) I search the file "libvirt-sock" in all file system but there is not file with this name.
 
(3) I remove with "apt-get remove qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils" and reistall its without success.

probably there a bug in the KVM installation procedure "https://help.ubuntu.com/community/KVM/Installation"  

Any suggestion?  Please help me.

---

### Post by antonello1 on 2011-10-23
I have not libvirtd deamon running......

---

### Post by gasbakid on 2012-08-28
i think you should uncomment the libvirtd.conf variable  unix_sock_dir and before that be sure that /usr/sbin libvirtd -d  is running.

---

