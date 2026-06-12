---
title: "kvm libvirt lvm VM consistent backup (online&amp;offline)"
date: 2011-04-12
forum: Server Platforms
---

### Post by pivert on 2011-04-12
Hi,

What are the solutions to consistently backup a set of VMs stored in disk images (qcow2 or raw) on a filesystem on a lvm volume (with possible snapshots).

- Online : Ideally, I would like to send a sync to all VMs before pause and snapshot, but it seems that it's not possible with KVM (it was with XEN). The save command seemed to be an option, but it crashes some VMs. So, what do you recommend to backup these VMs online ?

- Offline : Is there a command to shutdown all vms, and start them back after snapshot/backup ?

Regards,

---

### Post by KryptoKalEl on 2011-07-27
No answer anyone?
I'm going to be testing the following method for backing up KVM's installed directly onto LV's:
1. Take snapshot of LV
2. Mount snapshot
3. Copy mounted snapshot files to removable media(hotplugged SATA)
4. Remove snapshot

The above will be my daily routine.

As the guest OS is going to be Windows SBS2011, I'll run an Aconis Image internally (on the Guest) as well (weekly).

---

