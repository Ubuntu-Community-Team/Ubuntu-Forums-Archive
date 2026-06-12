---
title: "KVM migration error: unable to migrate the guest"
date: 2011-10-23
forum: Virtualisation
---

### Post by xueliangfei on 2011-10-23
Hi, ALL
I encounter a problem when I want to migrate a VM from localhost to the
remotehost(destination)
the error is
"Unable to migrate guest: unable to set user and group to '110:120'
on '/var/lib/libvirt/images/vm1.img'.'/var/lib/libvirt/images/vm1.img':No such
file or directory "
I do not know why.
I try
1  chmod 777 -R /var/lib/libvirt/images/
2  I can mount the same directory from the local to the remote host directory.
3  I use the system of ubuntu.  change the /etc/libvirt/qemu.conf
  uncomment the 'dynamic_ownership=0'
But all these are not helpful to the error.
Can you help me?
PS: I use the ubuntu server. How can I restart the libvirtd?
service libvirtd restart doesn't work.
The error is describe in the picture.
[IMG]http://blog.chinaunix.net/attachment/201110/23/26284395_1319378448R7WG.jpg[/IMG]

---

