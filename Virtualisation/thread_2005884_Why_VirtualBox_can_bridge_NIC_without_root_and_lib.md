---
title: "Why VirtualBox can bridge NIC without root and libvirt qemu:///session can not?"
date: 2012-06-18
forum: Virtualisation
---

### Post by kengi87 on 2012-06-18
Hi everybody, do you know how can I bridge a guest network interface with the host one with libvirt in qemu:///session without root privilege?
I'm working in depth on this problem, and I can't figure out a way to use something different from NAT (interface type="user") for my qemu VMs in session mode (with not-root user).
I know that VirtualBox can bridge Guest interfaces with the host one without root privilege! I wonder if this can be possible for libvirt qemu:///session too.

---

### Post by CharlesA on 2012-06-18
See here:
[http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking)

---

### Post by kengi87 on 2012-06-19
Thanks for reply. This is a slice of that article that you posted, about the bridging:

[I]Prerequisites:

You need kvm up and running
If you don't want to run as root, the user you want to use needs to have rw access to /dev/kvm
You need the following commands installed on your system, and if you don't want to run as root, the user you want to use needs to be able to sudo the following command:
/sbin/ip
/usr/sbin/brctl
/usr/sbin/tunctl
[/I]

These are really invasive prerequisites, I don't want to enable sudo for networking commands for each user. 

VirtualBox can create bridged networks without these requirements. Maybe with qemu-kvm, as you posted, this is the only one solution for this problem, but it's really strange that with VirtualBox I can do it and with kvm-qemu I can not.

---

### Post by CharlesA on 2012-06-19
You need to enable those commands for the user you want kvm running as, not each user.

You might be interested in this:
[http://ubuntuforums.org/showthread.php?t=1901158](http://ubuntuforums.org/showthread.php?t=1901158)

---

