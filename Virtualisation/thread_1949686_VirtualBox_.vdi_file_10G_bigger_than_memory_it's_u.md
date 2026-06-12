---
title: "VirtualBox .vdi file 10G bigger than memory it's using!"
date: 2012-03-30
forum: Virtualisation
---

### Post by skinns on 2012-03-30
Hi,

I'm using virtual box (version 4.0) in Ubuntu 11.10, running a Debian VM using a dynamic disk image.

Inside the Debian VM, `df` gives:

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              98G  8.9G   84G  10% /
tmpfs                 676M     0  676M   0% /lib/init/rw
udev                  671M  164K  671M   1% /dev
tmpfs                 676M     0  676M   0% /dev/shm


So it is using 8.9G, but the vdi file is 19GB. I've tried both of the following, which I found elsewhere, but compacting does barely anything and clone just produces a 19G clone:

vboxmanage modifyvdi vm.vdi compact

vboxmanage clonehd vm.vdi vm_clone.vdi

How can I reduce the size of the vdi file to match the amount of memory it's actually using?

---

### Post by Cheesemill on 2012-03-31
Have you got any other partitions on it, swap for example?
What is the output of:
```
sudo fdisk -l
```
inside the VM?

---

### Post by skinns on 2012-04-02
fdisk -l gives:

```
Disk /dev/sda: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004487e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12931   103862272   83  Linux
/dev/sda2           12931       13055      992257    5  Extended
/dev/sda5           12931       13055      992256   82  Linux swap / Solaris
```



So (correct me if I'm wrong here) it's still only using about 9G

---

