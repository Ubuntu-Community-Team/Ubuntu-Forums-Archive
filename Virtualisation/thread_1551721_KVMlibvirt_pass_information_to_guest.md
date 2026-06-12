---
title: "KVM/libvirt: pass information to guest"
date: 2010-08-12
forum: Virtualisation
---

### Post by pytheas22 on 2010-08-12
I'm building a virtual machine that will be used to back up other virtual machines.  My plan is to write a script on the host that boots the virtual machine with its primary disk as hda, along with a secondary disk from another virtual machine as hdb.  The backup machine will then mount the partitions on hdb and copy their data somewhere else using rsync or something--all pretty straightforward.

The problem I'm running into is figuring out a way for the guest machine to know which virtual disk it's backing up.  I have several virtual disks to back up, and I need to know which files on the backup media correspond to which disks.  I guess I could use UUIDs of the virtual disks, but ideally I'd like to have something more semantic, such as the name of the virtual machine with which the disk is associated.

I'm wondering, therefore, if there's any way for KVM or libvirt to pass information to the guest.  One thought is to try to pass a kernel boot parameter that I could then read from the guest by catting /proc/cmdline, but I'm not sure if that will work.

So, any suggestions on how I can have the host boot the guest with variable information that the guest can retrieve after it's live would be great.  I'm thinking there must be a way.

---

