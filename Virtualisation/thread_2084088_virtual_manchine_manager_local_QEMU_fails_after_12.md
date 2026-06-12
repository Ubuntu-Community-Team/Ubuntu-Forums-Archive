---
title: "virtual manchine manager local QEMU fails after 12.10 upgrade"
date: 2012-11-14
forum: Virtualisation
---

### Post by anamenottaken on 2012-11-14
After upgrading from 12.04 to 12.10 I'm facing two issues. First is that the Virtual Machine Manager is looking for the libvirt socket in /run/user/<USER>/libvirt/libvirt-sock instead of /var/run/libvirt/libvirt-sock

As a quick work-around, I make a symlink to the socket and can now connect to 'localhost ( QEMU Usermode)

However, my previously defined machines are gone! The images are on the disk, but they are not listed.

Where were these configs saved in 12.04?

---

### Post by markbl on 2012-11-15
> **anamenottaken said:**
> 
However, my previously defined machines are gone! The images are on the disk, but they are not listed.
I am watching this thread to see if anybody has an answer because I am seeing this same issue on 12.04.

I was using qemu at the command line to run a old Solaris guest VM but was having problems so I upgraded qemu from the ubuntu 12.04 package 1.0 version to current qemu 1.2 source version (which is also the version of qemu package in 12.10). That fixed the Solaris VM problem I was having but now I can not see my other debian guest VM which I had created and managed in virt-manager. It is not listed there anymore, although I do see the disk image etc in /var/lib/libvirt.

---

