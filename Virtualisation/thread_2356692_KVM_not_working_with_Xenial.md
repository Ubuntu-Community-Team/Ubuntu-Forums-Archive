---
title: "KVM not working with Xenial"
date: 2017-03-25
forum: Virtualisation
---

### Post by jrdbrndt on 2017-03-25
I have a VPS at OVH.ca and I'm attempting to install my own operating system, other than the ones they install for you. I boot it into rescue mode, which allows me to repartition and mount the disk and install Ubuntu using debootstrap. Then I try to boot it, and this is what I get:

[IMG]https://brndt.ca/20170325_174855.png[/IMG]

They obviously won't offer me any support, since I'm trying to install an OS other than the ones they provide. But I'm convinced it's a Xenial thing anyway, since it WORKS if I follow exactly the same steps to install a Debian OS or Ubuntu Trusty. This is the process I follow after booting into rescue mode with a Debian Jessie disc and adding the Stretch repository (for the latest debootstrap):

```

umount /mnt/sdb1   # it starts as mounted
rmdir /mnt/sdb1

fdisk /dev/sdb   # create a partition
mke2fs -t ext4 /dev/sdb1
mount /dev/sdb1 /mnt

apt-get -t stretch install debootstrap ubuntu-archive-keyring
debootstrap --variant=minbase xenial /mnt

```
EDIT: I use the latest version of debootstrap because the one in the Jessie repository doesn't include a script for Xenial.
Then, i chroot into /mnt and install:

```

apt-get -y install nano linux-image-generic-lts-xenial grub-pc net-tools ifupdown iproute2 ufw isc-dhcp-server ssh rsyslog
grub-install /dev/sdb
update-grub

```
EDIT: actually i do the install in two steps. I install nano first, then update /etc/fstab to include the root filesystem. Then in stall the kernel and grub and others. I have also tried installing the virtual version of the kernel. I have also trying including the recommended packages.

Then reboot, and I get that screen above. I can't SSH into it ("no route to host") either. Like I said, if I try this with a different OS, it works just fine. I've also tried building the OS on my machine and uploading it as a tar then extracting. I have tried another option as well (won't get into the details) but everything I try -- with Xenial -- gets me to that screen above. Since I don't have physical access to the machine, I can't actually see what a "real monitor" would look like.

EDIT: Just realized the reason I can't SSH in *may* be because I have yet to configure the network for DHCP in /etc/network/interfaces. I will reboot in rescue mode and configure and see if that changes anything...
EDIT: I am also going to try to install a different (previous) version of the kernel.
EDIT: I configured the network and installed a different (actually newer) kernel. So I've tried with 4.4.0-21 and 4.4.0-66. After configuring the network, I still cannot SSH into the machine.

Any thoughts on what might be happening here?

THANK YOU!

Jared

---

### Post by ajgreeny on 2017-03-26
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by jrdbrndt on 2017-03-26
I did not solve the problem, so I will not mark this as solved. But I found a temporary workaround. Instead of installing Xenial, I installed Trusty and then ran *do-release-upgrade*. It works.

Thanks everyone for your attention! :)

Jared

---

