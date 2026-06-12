---
title: "Recover .img backup from Vmware ESXi"
date: 2017-10-23
forum: Virtualisation
---

### Post by timahe on 2017-10-23
Hi,

I'm really straight on the hose and hope a clever head couldhelp me.
A backup was created from a VMware ESXi server using dd. Result: (large) .img file.
I need to get this restored in order to save the .vmdk files. At the disposal I have dedicated Ubuntu 16.04.
First I just tried to mount it (got offset number using parted)
> mount -o loop,ro,offset=123456 backup.img /mnt/root
Spits out the following error message:
> mount: unknown filesystem type 'VMFS_volume_member'

After that I came to vmfs-tools. Here, I can not mount an image (seems to work only with active disks, did not find anything via Google to get the image mounted).

Do you have an idea? In my despair, I've already try to do it using 
> dd if=backup.img of=/dev/sdXShoot me the Filesystem.
How else could I proceed?

Would be very grateful for any advice.

Best regards

---

### Post by TheFu on 2017-10-24
What was the dd command that you used?  Depending on the level where you did it, that will determine what level you must restore.  It appears you did the dd at the partition level or higher (disk?).  That means the entire file system, VMFS, was stored, not just the vmdk files.

I would restore to a new ESXi install from the same release.  Then I'd use normal Unix backup tools (not imaging tools) from inside each VM to perform backups like they were physical machines.  Then restore those backups as needed to either a physical machine or a VM running under a F/LOSS hypervisor like KVM.

---

