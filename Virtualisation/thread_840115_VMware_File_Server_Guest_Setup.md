---
title: "VMware File Server Guest Setup"
date: 2008-06-25
forum: Virtualisation
---

### Post by robgolding63 on 2008-06-25
Hi,
I am planning a new virtual server, which will host a file server/Active Directory DC, an Exchange Server, and a web server on an Ubuntu 8.04 host using VMware Server. I am struggling with the planning for the file server - due to performance considerations mostly.

Basically, I have 2 500GB SATA disks that I plan to incorporate into an mdadm RAID1 configuration. I then wish to expose this array to the File Server VM, one way or another. At present I have three options:

[LIST]
[*]Mount the array on the host and use a large .vmdk
[*]Attach the array as a raw disk to the VM
[*]Use iSCSI, with the target running on the host, and the initiator on the VM.
[/LIST]

I am having speed issued with the last 2 options - but I don't really want to go with the vmdk option, as I want to be able to get at the data easily if a failure occurs. Also, it would take a very long time to preallocate 500GB worth of virtual disk.

I am aware that .vmdk files can be mounted, however, using virtual disk tools, so I could access the data in the event of a failure. So this option is a possibility.

For further information, I am managing speeds of ~15MB/sec using a vmdk file, but only 9MB/sec using iSCSI or direct attached drive. This is all over a gigabit network, believe it or not. I would like to achieve faster speeds in all cases, but I can't see what's causing the slowness. I have a semi-enterprise switch (Netgear FSM726).

Any opinions on this matter would be greatly appreciated.

Thanks a lot,

Rob

---

