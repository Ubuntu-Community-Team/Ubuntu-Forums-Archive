---
title: "KVM: Soft Lockups in KVM 9.04 Guests after migration to 12.04 Host"
date: 2012-09-28
forum: Virtualisation
---

### Post by kindergartencop on 2012-09-28
Hi all,

I have several KVM Guests, running Ubuntu 9.04 on a 9.04 Host. 9.04 is not exactly top of the line anymore, so I decided to move to a 12.04 Host. The guest machines are locally accessible only, there is no immediate need for an update there.

Just after I moved the first 9.04 machine to the new host the GUEST began giving me strange ATA timeouts on the console, accompanied by  messages like "BUG: soft lockup - CPU#0 stuck for 95s! [scsi_eh_0:30]".

Of course, performance with those ATA timeouts and sticky CPU is intolerably bad. I started a guest VM with 12.04 and it did not exibit the problems. One of the more obvious differences between the (otherwise identically configured) machines, besides their kernel versions, of course, was this line in /proc/cpuinfo:


model name    : QEMU Virtual CPU version 1.0
on 12.04:
cpu MHz        : 3399.998
on 09.04:
cpu MHz        : 33999.980

I wonder if that may have something to do with it.

So much for easy migration of virtualized hosts.

Any ideas on how I can get those 9.04 guests running on the new host without having to upgrade all of them to 12.04?

---

### Post by kindergartencop on 2012-09-28
Just to let you know, I solved the problem by changing disks from ide to paravirtualized drivers like this:

[LIST]
[*]edit /etc/initramfs-tools/modules on guest and add virtio, virtio_pci, virtio_ring, virtio_net, virtio_blk
[*]edit fstab on guest (sda -> vda)
[*]update the initramfs on guest using update-initramfs -u
[*]in guest os, change /boot/grub/device.map from "(hd0) /dev/sda" to "(hd0) /dev/vda"
[*]in guest os, change /boot/grub/menu.list from "root=/dev/sdaX" to "root=/dev/vdaX"
[*]shutdown guest
[*]in virsh edit guest config to make the disk section look like this:
<disk type='...' device='disk'>
  ...
  <target dev='vda' bus='virtio'/>
</disk>
Especially, delete all "address" tags inside the disk section
[*]save config and start guest again.
[*] If it doesn't work, then check the following file in the host for errors: &#8232;
/var/log/libvirt/qemu/[guestname].log
A console may also come in handy (vnc)
[/LIST]
good luck.

---

