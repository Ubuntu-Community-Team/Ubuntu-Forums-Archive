---
title: "KVM / libvirt nightmare after upgrading to 9.10"
date: 2009-11-23
forum: Server Platforms
---

### Post by pivert on 2009-11-23
After upgrading my virtualization server from 9.04 to 9.10, most of my VM refuses to start. I have many different error messages. I also applied the latest updates to new kernel 2.6.31-15-generic-pae and latest libvirt :
root@homer2:/etc/libvirt/qemu# virsh version
setlocale: No such file or directory
Connecting to uri: qemu:///system
Compiled against library: libvir 0.7.0
Using library: libvir 0.7.0
Using API: QEMU 0.7.0
Running hypervisor: QEMU 0.11.0

Here is the status of some of my VMs :
- Only one VM works correctly, this is an old Gentoo VM, using no virtio drivers.
- Ubuntu server 9.04 : stops with 100% CPU with "request_module: runaway loop modprobe binfmt-0000" message. Even after changing the xml config to match exactly the same options than the working Gentoo VM.
- On an 8.04 LTS, I'm just droped into initramfs Busybox because of an "ext3_check_descriptors: Block bitmap for group 0 not in group (block ... )"error
- On an other 9.04, I have a "run-init: /sbin/init: Accessing a corrupted shared library" error just before a Kernel Panic.
- Old gentoo :  with no virtio in config file, I just have a "no init found" kernel panic.
- Old gentoo : on this last Gentoo VM, I have an error during the mount command : /lib/libblkid.so.1: invalid ELF header.
- A fresh install of 9.10 VM seems to work perfectly with virtio drivers (default).

All these VM were running for years on my Ubuntu 9.04 2 days ago, before the upgrade to 9.10.

What is this mess ? How do I get back the VMs ? Why so many different behaviors depending of the distrib/kernel ?

Regards,

---

### Post by pivert on 2009-11-26
Hi,

I can't believe I'm the only one to get this problem. I tried on 2 different hosts (AMD & Intel VT), and got the same results. Here are the step to reproduce :

- Create araw disk image with qemu-img ... 
- Download the ubuntu-8.04.2-server-i386.iso image
- as root : kvm -hda ./akira4.img -cdrom ./ubuntu-8.04.2-server-i386.iso  -boot c -m 512M -net none
- Install the Ubuntu 8.04. (Avoid LVM because it will fail.)
- The OS will never boot once installed, and you will get the error :

run-init: /sbin/init: Accessing a corrupted shared library
then a Kernel panic...

---

### Post by chrroessner on 2009-12-01
Unfortunately you are not alone with this problem. I do have exactly the same problem here.

Host system was 9.04 and all guests, too.
Was running without problems for months.

Upgraded the host and now I can not start any guests anymore.

I get the same errors that you described above.

Anybody any ideas on that?

---

### Post by chrroessner on 2009-12-01
Update:

The problem that I have is under 32bit mode on an AMD.

I also have an Intel Core Quad, which also runs under 9.10 with two guests 9.04. There are no problems. The guests are running fine. So I checked the differences. The Intel machine is completely 64bit, while the kernel of the 64bit AMD only is generic-pae 32bit.

AMD-host:
linux-image-generic-pae (32bit)
Guests:
linux-image-server (32bit)

Intel-host:
linux-image-generic (64bit)
Guests:
linux-image-server (64bit)

So this seems to be the problem. I am also _not_ using libvirt. Instead kvm directly. The settings are completely the same.

What has happend to the linux-image-generic-pae that it now causes these problems in 32bit mode?

---

### Post by chrroessner on 2009-12-01
[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/490732](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/490732)

---

