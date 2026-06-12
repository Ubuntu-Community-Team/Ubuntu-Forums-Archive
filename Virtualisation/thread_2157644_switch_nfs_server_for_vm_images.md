---
title: "switch nfs server for vm images"
date: 2013-06-26
forum: Virtualisation
---

### Post by JosMuysers on 2013-06-26
On a 12.04 server we run 5 vm's off a nfs share. we have 2 nfs storage servers (debian 6), the storage is mirrorred using drbd.
I would like to switch nfs servers for maintanance without rebooting the vm's.

This is what I did:
- suspend the vm's (virsh suspend <vm>)
- unmount the nfs share (umount /mnt/images)
- make primary and mount the mirrored drbd partition (drbdadm primary r0, mount /dev/drbd0 /nfs/images)
- point dns to the second server ip
- mount the same share from the second server (mount data:/nfs/images /mnt/images)
- resume the vm's (virsh resume <vm>)

The vm's will run, but all the filesystems in the vm's are now read only. Why does this happen?
Is there a better way to switch storage servers without rebooting the vm's? (a few minutes of downtime is acceptable)

---

