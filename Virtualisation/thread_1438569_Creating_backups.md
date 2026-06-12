---
title: "Creating backups?"
date: 2010-03-25
forum: Virtualisation
---

### Post by c0dem4gnetic on 2010-03-25
Im using virsh and whatnot (libvirt? kvm? qemu?) and are looking for recommendations on how to create off-site, daily, backups of my machines. As I see it it is not enough to just copy the images but also the machine specifications and this is where I'm at a loss. Are there any utilities that can help me? Perhaps virsh supports this natively just that I havn't found it? How do you create backups?

Any hints or tips are very much appreciated!

---

### Post by codfather on 2010-03-25
It depends on the storage you are using, as most NAS/SAN type arrays support snapshots, which would allow you to create an image backup and then store that on removable media for off-site storage or even use something like rsync to copy off the snapshots across your WAN.

If the disk's are all local, then unless you are going to use a third party product , you are probably best to use one of the many backup utils that Ubuntu supports, and just make sure you specify the config directories as well as the disk image files. Make sure you have suspended the image you wish to backup otherwise the backups will not be correct.

If the VM doesn't intrinsically change regularly, but it is the data served by the application, then you might be better off backing up the VM once a month, and using a standard backup util's for the application. VM's tend to be very large and doing will take up a lot of storage as well as time to back them up.

---

### Post by TheFu on 2010-03-26
We use a custom rdiff-backup script to pause each VM, mount it from the hostOS/Dom0, rdiff-backup to another machine on the LAN (nearby backup), unmount the VM.img, unpause each VM. then use rsync to remote the local backup to an offsite location. The local rdiff-backup part usually takes 1-3 minutes per VM per day.   We're small and prefer to use Full IMG files, not sparse, not compressed or LVM.

Recovery has been proven too .. er, a few more times that I'd like.

In an enterprise I'd look at ZFS and zsend to push remotely. LVM2 snapshots could make sense if you were already using LVM.

---

