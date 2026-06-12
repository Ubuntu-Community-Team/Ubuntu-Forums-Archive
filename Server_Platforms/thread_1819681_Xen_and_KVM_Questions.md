---
title: "Xen and KVM Questions"
date: 2011-08-06
forum: Server Platforms
---

### Post by pneumatic on 2011-08-06
I'm not real happy with VMware's new licensing greed so I am in need of moving my employer's systems to something else.  I'd like to investigate Xen and/or KVM but I can't find any comprehensive list of features on either.  I hope that this glaring oversight on the part of both projects is not indicative of the quality.

Can someone speak to the following?


[LIST=1]
[*]Live storage migration (i.e. - moving a running disk from Shared Storage A to Shared Storage B)
[*]Online disk resizing (i.e. - adding space to a virtual disk as it fills up without shutting it down)
[*]Online snapshot management (i.e. - take a snapshot on Wednesday, make changes to the running machine and then revert them to the snapshot)
[/LIST]
This is pretty much all that I need.  No sense in paying VMware through the nose for it at this point.

Any help is appreciated.

---

### Post by TheR on 2011-08-07
These is pretty hard stuff. I can only replay for KVM.

[LIST=1]
[*]Live storage migration (i.e. - moving a running disk from Shared Storage A to Shared Storage B)

I think I read somewhere that this is going to be one of the priorities for next verison.


[*]Online disk resizing (i.e. - adding space to a virtual disk as it fills up without shutting it down)

This can be done. Although not automagicaly (maybe with Eucalyptus).

[*]Online snapshot management (i.e. - take a snapshot on Wednesday, make changes to the running machine and then revert them to the snapshot)

This one is easy with lvm volumes. But then again, by hand. No automagic.

[/LIST]

I wonder does VMWare support all these features on local machine or also on SAN iScsi storage servers.

by
TheR

---

### Post by pneumatic on 2011-08-09
VMware supports all of this stuff.  I can move a live virtual machine to different storage (or to a different host).  I can also increase the disk space of a virtual machine without shutting it down.

I can also hotplug RAM and CPU on VMs with operating systems that support such an operation.

VMware recently backed off on their greed a little bit (they are giving more RAM before you have to pay) so this buys me some time.  Hopefully, with Xen running on the default kernel, we'll see these features brought in before I get to the point where VMware is going to cost big bucks.

---

### Post by tvijlbrief on 2011-08-10
On 11.04 migration of KVM virtual machines works like a charm, but you'll
normally migrate either just the VM (and storage is shared between source and destination host)
or VM and physical disk images together:

Just type:

migrate --live --copy-storage-all SrcVm qemu+tcp://root@destmachine/system --persistent

in virsh (or use the migrate option in virt-manager GUI if you have shared storage).

I can do this while being remotely logged on on the guest SrcVm (it's my IPv6 gateway/webserver) and from SrcVm I am running an SSH session on my VM-host where I give the migrate command.

It's really cool. All network sessions continue.

If you want just to move the storage and leave the VM on it's original host then you'll have to implement a distributed file storage feature on the host(s) and/or your network.

I have no experience with resizing harddisk storage images without shutting down the guest. You would need special guest drivers and OS support in the first place, because real world physical disks don't grow without being replaced, which requires a reboot. Perhaps virtio block drivers offer a sollution.

Note that it should be possible to ADD devices (eg disks+controllers) with PCI hot-plugging: [http://www.linux-kvm.org/page/Hotadd_pci_devices](http://www.linux-kvm.org/page/Hotadd_pci_devices), but never tried that. You might be able to remove a simulated SCSI disk and replace it with a bigger one, but obviously not with active filesystems on it.

In many situations you can access SMB or NFS storage servers from the guest and grow the storage servers filesystems instead of the smaller fixed HD images from which the guests are booted.

---

### Post by pneumatic on 2011-08-12
Thanks.

Part of my desire is to get ATA over Ethernet AoE based storage.  Since it is datagram-based transport, you can simply aggregate links to get more bandwidth.  With TCP-based technologies, a single conversation has to take place on a single port - so even with aggregate links, a single transfer is limited by the speed of a single port.

VMware seems to be catering to their high-dollar storage vendors.  If they would just support AoE natively, then iSCSI, FCoE and NFS would largely go away for all but the big players.

So Xen or KVM on linux allows me to build two giant storage boxes and simply configure an AoE RAID1.  If I put 8 gigabit ports on each server, then I get 8 gigabit of bandwidth allowed for any single transfer (and obviously shared with others).

This is a dramatic improvement over my current 8x1 gigabit NFS and costs less than $1000 versus $20k for 10 gigabit NICs and switches.

I am testing Xen now - I can pull the plug on one of the storage boxes during an 750 *megabytes* per second data transfer with no corruption.  You can't get that from VMware for less than $200,000.

I just need the other features to catch up slightly - not much.  Then we can dump VMware.

---

### Post by matthew.mattoon on 2011-10-12
> **pneumatic said:**
> Thanks.

Part of my desire is to get ATA over Ethernet AoE based storage.  Since it is datagram-based transport, you can simply aggregate links to get more bandwidth.  With TCP-based technologies, a single conversation has to take place on a single port - so even with aggregate links, a single transfer is limited by the speed of a single port.

VMware seems to be catering to their high-dollar storage vendors.  If they would just support AoE natively, then iSCSI, FCoE and NFS would largely go away for all but the big players.

So Xen or KVM on linux allows me to build two giant storage boxes and simply configure an AoE RAID1.  If I put 8 gigabit ports on each server, then I get 8 gigabit of bandwidth allowed for any single transfer (and obviously shared with others).

This is a dramatic improvement over my current 8x1 gigabit NFS and costs less than $1000 versus $20k for 10 gigabit NICs and switches.

I am testing Xen now - I can pull the plug on one of the storage boxes during an 750 *megabytes* per second data transfer with no corruption.  You can't get that from VMware for less than $200,000.

I just need the other features to catch up slightly - not much.  Then we can dump VMware.

Hi pneumatic,

We went through similar growing pains with relation to our storage and we really strongly considered AoE for a while, we ended up deciding against it because of the lack of security to protect the storage devices on the storage network.  Ultimately that was a huge scalability problem for us.  Instead we decided to build a custom fibre channel SAN.  And frankly it was exactly what the doctor ordered.  A few links to my blog which contain some of the nuts and bolts of "rolling your own".

A Primer on ZFS which is what enables the whole solution:
[http://blog.allanglesit.com/2011/04/so-you-want-to-learn-zfs-part-one/](http://blog.allanglesit.com/2011/04/so-you-want-to-learn-zfs-part-one/)

My whole ZFS category
[http://blog.allanglesit.com/topics/platforms/storage-platforms/zfs/](http://blog.allanglesit.com/topics/platforms/storage-platforms/zfs/)

The most difficult part of rolling your own is configuring the Fibre Channel Targets
[http://blog.allanglesit.com/2011/08/adventures-in-zfs-configuring-fibre-channel-targets/](http://blog.allanglesit.com/2011/08/adventures-in-zfs-configuring-fibre-channel-targets/)

-matt

---

