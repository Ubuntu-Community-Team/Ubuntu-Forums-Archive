---
title: "AppArmor messing with KVM"
date: 2024-10-24
forum: Virtualisation
---

### Post by gbwebdev on 2024-10-24
I installed a new Ubuntu Server 24.04.

I try to create a VM with the following command :
```
virt-install --import --name my-vm --memory 3072 --vcpus 2 --cpu host --disk /usr/lib/libvirt/images/my-vm/disk.qcow2,format=qcow2,bus=virtio  --os-variant=ubuntu24.04 --graphics spice --noautoconsole
```

But I get the following error :
```
Starting install...
ERROR    internal error: cannot load AppArmor profile 'libvirt-24b161d1-591e-4105-95d8-b666979c04d0'
Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start my-vm
otherwise, please restart your installation.

```

In the logs, I can see :
```

Oct 24 18:51:30 main-server libvirtd[120558]: internal error: cannot load AppArmor profile 'libvirt-5185dc02-c828-4c16-8b48-9deeaca23945'
Oct 24 18:51:30 main-server libvirtd[120558]: internal error: Child process (LIBVIRT_LOG_OUTPUTS=3:stderr /usr/lib/libvirt/virt-aa-helper -c -u libvirt-24b161d1-591e-4105-95d8-b666979c04d0) unexpected exit status 1: virt-aa-helper: error: /usr/lib/libvirt/images/my-vm/disk.qcow2
                                              virt-aa-helper: error: skipped restricted file
                                              virt-aa-helper: error: invalid VM definition

```

```

$ ls -la /usr/lib/libvirt/images/my-vm/
total 580
drwxr-xr-x 2 libvirt-qemu kvm   4096 Oct 23 18:34 .
drwxr-xr-x 3 libvirt-qemu kvm   4096 Oct 23 18:13 ..
-rw-r--r-- 1 libvirt-qemu kvm 374784 Oct 23 18:34 cidata.iso
-rw-r--r-- 1 libvirt-qemu kvm 197248 Oct 23 18:33 disk.qcow2
-rw-r--r-- 1 libvirt-qemu kvm     51 Oct 23 17:57 meta-data
-rw-r--r-- 1 libvirt-qemu kvm   1037 Oct 23 18:08 user-data

```


I tried to add the following to :
- /etc/apparmor.d/local/usr.lib.libvirt.virt-aa-helper
- 
```

  /usr/lib/libvirt/images/**/*qcow2 rwk,
  /usr/lib/libvirt/images/my-vm/disk.qcow2 rwk,

```
And restart AppArmor, but it changes nothing.

I even tried to set complain mode : 
```
aa-complain /usr/sbin/libvirtd
```
And nothing changes.

I started to think that AppArmor was not even the cause but then I simply tried to set ```
ecurity_driver = "none"
``` in /etc/libvirt/qemu.conf... And it works.

At this point I must confess that I am running out of ideas...

---

