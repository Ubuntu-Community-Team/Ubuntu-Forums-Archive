---
title: "VMbuilder not installing to LVM"
date: 2010-05-16
forum: Virtualisation
---

### Post by cldfzn on 2010-05-16
I'm attempting to set up my virtual machines using this command:

sudo lvcreate -L 3512 -n CHANGEME vg-vm; sudo vmbuilder kvm ubuntu --suite lucid --flavour virtual --arch amd64 -o --libvirt qemu:///system --ip 10.10.10.3 --gw 10.10.10.1 --dns 10.10.10.2 --part vmbuilder.partition --raw /dev/vg-vm/CHANGEME --bridge br0 --hostname HOSTNAME --mem 512 --user USERNAME --pass PASSWORD --addpkg acpid;

But it installs my vm to a qcow img on my local hard disk instead of onto the logical volume I just created.  I imagine I'm doing something wrong but I don't see it.

---

### Post by cldfzn on 2010-05-16
Anybody?

---

### Post by tekknokrat on 2010-06-09
Hi,

I am pointing you to this [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests).

Please look at "Install on a raw block device". 

Just change the blockdevice to your lv path /dev/vgXX/lvname.

---

### Post by sbike on 2011-01-14
--raw used to either not exist or was broken.  Thus requiring writing a qcow file locally then converting it to raw and writing it to the LVM.

Using --raw=/dev/vgXX/lvname and now works.

Quite a time saver, now vmbuilder is much more useful.

---

### Post by David Alfonso on 2011-08-23
I've been trying to build a VM on a raw lvm logical volume device using VMBuilder and the --raw command, but it has turned out impossible for me. I am using Ubuntu 11.04 as my host system.

The error shown was:

```

Process (['parted', '--script', '--', '/dev/vg01/vm', 'mkpart', 'primary', 'ext2', '63s', '3999']) 
 returned -11. stdout: , stderr: device-mapper: deps ioctl failed: No such device or address

```The execution parameters were:
```

sudo vmbuilder kvm ubuntu
          --suite=lucid 
          --flavour=virtual 
          --arch=i386 
          --mem=1024 
          --hostname=vm_jeos 
          -o --libvirt qemu:///system 
          --bridge=br0 
          --ip=172.16.0.2 --mask=255.255.0.0 --gw=172.16.0.1 
          --raw=/dev/vg01/vm
          --rootsize=4000 
          --swapsize=1000 
          --addpkg=acpid 
          --addpkg=openssh-server

```

This is just to say that the --raw parameter doesn't seem to work as well as commented...

---

