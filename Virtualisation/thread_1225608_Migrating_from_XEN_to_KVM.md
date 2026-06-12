---
title: "Migrating from XEN to KVM"
date: 2009-07-28
forum: Virtualisation
---

### Post by SergeiFranco on 2009-07-28
Hello, I am doing research on migrating from XEN to KVM.
There are various reasons (theoretical) why KVM would be an advantage.
I have followed this guide: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
Unfortunately many things are not explained there.
I am trying to create the virtual machine with the following command:
```

ubuntu-vm-builder kvm jaunty --domain 'somedomain' --arch 'i386' --hostname 'somehostname' --mem '2048' --rootsize '10240' --swapsize '2048' --components 'main,universe,restricted' --addpkg 'emacs openssh-server' --libvirt 'qemu:///system'

```

I have the following questions as I am currently stuck on many things.

1) In XEN we have LVMs for root and swap partitions.
How do I achieve similar setup? It is far easier to resize and LVM with XFS then LVM with a partition table inside.

2) How do I specify XFS file system?

3) The command line from above is getting stuck indefinitely with following progress:
```
2009-07-29 10:47:53,411 INFO     Creating disk image: /tmp/vmbuildertcOWzv/disk0.img
2009-07-29 10:47:53,417 INFO     Adding partition table to disk image: /tmp/vmbuildertcOWzv/disk0.img
2009-07-29 10:47:53,446 INFO     Adding type 1 partition to disk image: /tmp/vmbuildertcOWzv/disk0.img
2009-07-29 10:47:53,465 INFO     Adding type 3 partition to disk image: /tmp/vmbuildertcOWzv/disk0.img
2009-07-29 10:47:53,490 INFO     Creating loop devices corresponding to the created partitions
2009-07-29 10:47:53,499 INFO     Creating file systems
2009-07-29 10:47:53,502 INFO     mke2fs 1.41.4 (27-Jan-2009)
2009-07-29 10:47:54,354 INFO     Mounting target filesystems
2009-07-29 10:47:54,366 INFO     Installing guest operating system. This might take some time...
```
"This might take some time..." is approaching forever (and server is idling at same time).

Right now I am trying to create a new blank VM to see how it performs....

Could someone advise if KVM is actually a complete and functional product?

The server is in question is 2x Quad Core Xeon E5506 @ 2.13GHz with 16GB of Ram, running 2.6.28-13-generic #45-Ubuntu SMP x86_64 GNU/Linux, virtualisation is enabled from BIOS.

---

### Post by juancarlospaco on 2009-07-28
Add **--debug** and you will see the progress, it download package by package from repos.

KVM is a complete and functional product.

If you get confused, install Convirt 1.1 on admin machine, and you have a nice GUI.

Consider creating a Local Repo, to deploy VMs more quickly.

---

### Post by SergeiFranco on 2009-07-29
Thank you for you reply.

The guide I was using was out-dated,
I have installed vmbuilder and ran this: 
```
vmbuilder kvm ubuntu --domain 'somedomain' --arch i386 --hostname 'somehostname' --mem '2048' --rootsize '10240' --swapsize '2048' --components 'main,universe,restricted' --libvirt 'qemu:///system'
```
and rest has worked as in virsh guide.

Now. back to original questions, I can start/create VMs, but:

1) In XEN we have LVMs for root and swap partitions.
How do I achieve similar setup?*

2) How do I specify XFS file system?

* separate LVM volume for swap and root, and perhaps data volume if necessary.

---

### Post by juancarlospaco on 2009-07-29
You can do that on Installation of Guest OS.

BTW KVM and Ubuntu VM Builder are separate projects.

its not mandatory to use Ubuntu VM Builder with KVM, 
install Guest OS configuring LVM, encrypt, RAID, XFS or what do you want to

---

### Post by SergeiFranco on 2009-07-29
Ok, I understand the difference between kvm and vmbuilder,

next question would be - what is the equivalent of the following:

```
xen-create-image --dist=$dist --debootstrap --hostname=$hostname --force --passwd --size=10G --swap=1G --lvm=vg00 --mirror=http://ftp.nz.debian.org/debian --mem=$mem --fs=xfs 
```

Also what is the proper way of managing guests with kvm?
I am trying virsh but it looks like it can't even reboot guests:

```

virsh # reboot somehostname
error: Failed to reboot domain somehostname
error: this function is not supported by the hypervisor: virDomainReboot
```

Also another question, how to get console without gui (what is the eqivalent of "xm console")?

Thank you very much for your answer, your help is highly appreciated.

---

### Post by juancarlospaco on 2009-07-30
> **SergeiFranco said:**
> 
Also what is the proper way of managing guests with kvm?

Also another question, how to get console without gui 


Convirt is the proper way of managing guests with kvm.

I get console without gui via SSH, 
but can be VNC too, but i don't like.

---

