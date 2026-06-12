---
title: "VMware Server, best way to access RAID storage? SCSI passthrough?"
date: 2009-09-16
forum: Virtualisation
---

### Post by batfastad on 2009-09-16
Hi everyone

I'm planning to consolidate 2 physical servers onto a new box using VMware Server.
The 2 servers are a combined intranet DB/NAS unit running samba/netatalk/mysql/apache/postfix and the other is a new Zimbra mail installation.
I'm planning to use our 3Ware 9690SA-8i card in the new box and divide it into 2 arrays... 5x1TB in a RAID 6 for NAS/intranet storage and a 2x1TB in a RAID 1 for Zimbra mail storage. Then a final 1TB drive as a hot-spare.
I'll have 8GB physical memory and a quad core xeon powering the thing. And a redundant power supply in there as well. These virtual servers will be used by 10-15 users.
My main motivation for using VMs is not for improved portability (being able to move a VM to new hardware in case of failure) because both VMs will be tied to the hardware since they'll both need access to the storage provided by the 3Ware RAID card.
I want to use VMs so I can have all these running on a single beast box and both making use of our hardware RAID card.

I also want to try and set up 802.3ad link aggregation/bonding with LACP to turn the 2 NICs on the motherboard into a single 2gbps link. ESXi doesn't allow you to do mode 4 LACP ethernet bonding. We have a Netgear GSM7224 managed layer 2 switch and this is a feature I've always wanted to mess about with.

But I'm not sure what the best plan is to allow the VMs access to the arrays created by the 3Ware card.
Here's what I think the options are:

1) Using VMware Server just use the SCSI pass through feature to allow the VMs to access the partitions as regular sdb1/sdb2 drives. The host OS will have the 3Ware drivers installed so the arrays will just appear to the VMs as regular drives.
Pros: Using single hardware. Easy to set-up. Gives access to the 3Ware 3DM2 management interface.
Cons: ?performance hit and risk of data corruption using SCSI passthrough??

2) Set up a separate box with the 3Ware card and format the arrays as NFS, then mount those from within the VMs so it runs as a sort of SAN over our gigabit network. Then use ESXi as the host OS.
Pros: Gives access to the 3Ware 3DM2 management interface. Takes the storage away from VMware software. ESXi sounds much easier to set-up and manage than VMware Server. Near native performance of VMs.
Cons: Extra hardware node required to run SAN. Slightly complex to set up (never used NFS or SAN setups before). ?Performance hit when using a SAN over gigabit network?

3) Use ESXi and integrate the 3Ware drivers to access the arrays natively as regular sdbx drives. And rely on the 3Ware BIOS utility for management/monitoring
Pros: Takes the storage away from VMware software. ESXi sounds much easier to set-up and manage than VMware Server. Near native performance of VMs.
Cons: No access to 3Ware 3DM2 management interface as ESXi doesn't allow you to install other software/services. No on-the-fly RAID performance tweaking by the 3Ware 3DM2 utility

4) Like option 1 using VMware Server but just create a big virtual disk filling each of the arrays.
Pros: ?Better performance than SCSI passthrough? Simpler logical design.
Cons: If something happens to the VM virtual disk then that's a problem... with 1/2/3 above you can just mount the arrays on another machine/OS installation and everything should be readable.

I'd like to steer away from the idea of #4, I'm not keen on the idea of creating a 3TB virtual disk and having our whole installation/data locked in that vmdk file. With option #1 at least it's just the samba/netatalk/apache/mysql/postfix configurations which are locked inside the VM... and we can reload those from backups and have a fresh installation of that running within 30mins. The data is just stored on a regular ext3 partition or something which can just be mounted on any machine/installation.

It seems to me that option #1 is the best/easiest. But I'm concerned about this SCSI passthrough,
Does anyone have any experience of using the SCSI passthrough feature?
Is it reliable enough and is performance good enough for something like this?
I don't want the SCSI passthrough of VMware Server to munge all the data it's reading and writing.

Any comments / suggestions on this?

Cheers, B

---

### Post by PilotJLR on 2009-09-16
Absolutely option #2. VMware Server is quite slow, and offers particularly poor i/o performance. ESXi is a better choice. You can simply export the storage using NFS to the ESXi host.

I would stay away from LACP, since it is unlikely to help you. The low quantity of large SATA drives you have won't be able to even approach gigabit speed, let alone 2 gig speed. Your bottleneck here will likely be storage... with 2 VM's, I doubt it will be a problem, however it would also make link aggregation relatively useless.

Instead, use a NIC team, which offers redundancy and outbound load balancing with no upstream switch config. Having said that, consider adding a dual port GigE NIC to the ESXi, as you really shouldn't have both NICs teamed to the same board (SPoF).
If you do want to explore LACP, though, read this first:
[http://blog.scottlowe.org/2008/07/16/understanding-nic-utilization-in-vmware-esx/](http://blog.scottlowe.org/2008/07/16/understanding-nic-utilization-in-vmware-esx/)

I know it works on Cisco... I've never tried with Netgear.

---

### Post by batfastad on 2009-09-18
Thanks for the reply PilotJLR
Glad I asked before plunging in to the VMware Server route! :D

#2 does sound the best and most logical way to do it. And I get to set up a small SAN as well (cool)! I really like the idea of keeping the storage completely out of the clutches of VMware and on separate hardware. Means I can run the 3Ware 3DM2 monitoring software on the SAN box also.
But I have a few more questions.

1) So even with a single gigabit connection to the SAN, that should be more than enough throughput to deal with 2 VMs constantly accessing the 2 arrays?
One VM will be a Zimbra mail server which will probably be hammering the RAID 1 array with MySQL queries... is a single gigabit up to the task?

2) Exporting the storage as NFS from the storage box. How exactly do I do this?
Does that mean formatting the arrays as NFS? At the moment they are ext3.
Or is it more like running an NFS daemon to share the arrays out, then mounting them in the VMs fstab so the VMs see them as regular sdb1 etc devices?

3) SAN box specs.
We'll need to buy another new motherboard/processor to go in the SAN box. The only motherboard we have that has PCI Express is our excellent Tyan one with the quad core Xeon which is earmarked for the VM host... would be a shame to waste that in the SAN box.
I guess processor/memory doesn't have to be mega-power for just exporting NFS storage. 1GB of ECC memory, dual gbE NIC card, low-end dual-core processor. Any other suggestions?

4) Networking.
I don't know anything about Cisco terminology and I've never used link aggregation/ethernet bonding before... but since our Netgear switch supports it it's definitely something I'm interested in trying out!
It's a real shame ESXi doesn't support full 802.3ad with LACP... mode 4 per this wiki [https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation)

I'd love to have dual gbE bonded NICs on the SAN box going to dual gbE bonded NICs on the Vserver box on a separate VLAN. Then another pair of dual gbE bonded NICs from the Vserver to the rest of the network.

So basically ESXi only supports static/manual link aggregation

Would I be better off going with another hypervisor if I want link aggregation with LACP?
Xen or KVM or something?

Cheers, B

---

### Post by PilotJLR on 2009-09-18
Hi there,
I missed the fact that you're using whiteboxes... one possible problem would be compatibility with ESXi. Unlike Linux or Windows, there is basically nothing you can do to resolve incompatible hardware. I'm not saying your hardware won't work... just that you would need to install ESXi and verify the network, disk, etc, are all detected. It will be immediately obvious if something is not working. Since it's a whitebox, it's not "officially" supported.
For test purposes, I have a couple whiteboxes with ESX 4.0. They work fine, although I did pay attention to what chipsets everything used when buying them.

#1 - gigabit is more than up for the task, since your disks are the slow things here. If performance is poor on the database, it will be because large SATA disks are basically archival media and are not intended for high iops workload. In my real job, I only use SAS or FC disk for this purpose. You might have enough iops here, given the small user count, but it's a certainty that your disk will bottleneck long before the gigabit does. This is also the reason why LACP is not useful here. 


#2 - install nfs-common, then export a directory on your filesystem in /etc/exports. The underlying filesystem is up to you and will not be perceived by the ESXi host. Keep in mind NFS is a NAS technology, so the storage server filesystem is a lower level.

#3 - I agree. Of course, use redundancy (PSU, etc) whenever possible. Run as few services on the box as you can. Probably only ssh and nfs.

#4 - ESXi **does** support LACP; read the blog link I posted, as it describes it more detail and provides configuration examples. It simply has to be configured. But again, this will be a pointless exercise and will only add complexity; unnecessary complexity is the path to trouble! You won't be able to fill a 1 Gb pipe, much less 2 Gb. Instead, consider using ESXi teaming to implement redundancy.

---

### Post by dcstar on 2009-09-19
> **batfastad said:**
> Hi everyone

I'm planning to consolidate 2 physical servers onto a new box using VMware Server.
.........
I want to use VMs so I can have all these running on a single beast box and both making use of our hardware RAID card.
.........
Any comments / suggestions on this?

Cheers, B

I do not understand this whole question.

Any VM has whatever access** you** set up to the host resources, whether they be storage, network access whatever.

If you set up the VMs to use the filesystems you set up on the RAID card then they will be using the RAID card - via the host (as all VMs do).

The same applies to any teamed network cards - all of this is done on the host and any VM just sees a standard network connection.

The whole point about Server Consolidation/VMs is to have the host manage the hardware, not the VMs.

---

### Post by PilotJLR on 2009-09-20
I believe the point of the OP's post is to determine where and how the resources will be managed. Guests may behave the same, but hypervisors do not, which is why he's asking for feedback on where to manage his storage.

So what it comes down to is whether to use local RAID to present vmdk's over ext3 (or whatever else) to the guests with a hosted hypervisor... or to use a bare metal hypervisor and present vmdk's over NFS. You can see my preference here.

---

### Post by batfastad on 2009-09-20
Yeah my question was trying to focus more on what the best way to access the storage, since there's a few different ways.

I was concerned about the performance and reliability of the SCSI passthrough method.
And I didn't want to just create one huge 3TB VMware virtual disk.
But I still wanted to be able to run the 3Ware 3DM2 management service which isn't possible with ESXi
So the sort of "mini SAN" NFS export method sounds the best.

I'm looking at possibly going for OpenVZ instead of VMware/ESXi though

---

### Post by batfastad on 2009-09-21
And as an extra bit of info I'm now looking into iSCSI rather than NFS.
Apparently iSCSI would give much better performance for Zimbra

---

