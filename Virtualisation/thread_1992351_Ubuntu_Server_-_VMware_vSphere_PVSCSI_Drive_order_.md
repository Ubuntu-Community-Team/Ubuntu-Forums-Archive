---
title: "Ubuntu Server - VMware vSphere PVSCSI Drive order - UDEV rules?"
date: 2012-05-31
forum: Virtualisation
---

### Post by techstig on 2012-05-31
Hello all,

I've been working on creating a virtual storage appliance based on Ubuntu Server, DRBD, SCST-iSCSI, Pacemaker, Corosync, etc. running on vSphere 5 and have been successful so far. When finished I'll be happy to share my recipe. 

Only issue I have is that the OS always starts assigning /dev/sd* to the PVSCSI drives first. So...

```
LSI Parallel - For boot/OS
Disk1 = /dev/sdc
Disk2 = /dev/sdd

PVSCSI - For drbd
Disk3 = /dev/sda
Disk4 = /dev/sdb
```

No matter what SCSI ID I assign the drives (in VMware), Disk3 and Disk4 always end up as /dev/sda and /dev/sdb respectfully. This is fine if I leave this as it is. However if I later need to add 2 more disks to the PVSCSI adapter I get the following...

```
LSI Parallel - For boot/OS
Disk1 = /dev/sde
Disk2 = /dev/sdf

PVSCSI - For drbd
Disk3 = /dev/sda
Disk4 = /dev/sdb
Disk5 = /dev/sdc
Disk6 = /dev/sdd
```

I know this shouldn't be an issue since the OS drives are referenced in fstab by UUID and I *can* create the DRBD vols through /dev/disk/by-id/* references or use LVM. However, I was also trying to incorporate LCMC for graphical access to the clusters for others later down the road (that don't know how the magic works) to be able to figure things out quickly. However, LCMC will not use the /dev/disk/by-id/* references as of yet. Also, it's a little easier for others to understand that /dev/sda & /dev/sdb are OS, others are data/metadata. Also also, I am a bit worried that if I add a 3rd or 4th disk to the pvscsi adapter that sometime down the road it mixes up sdb and sdd... and thus could possibly (worst case scenario) contaminate the cluster or (best case scenario) require a full resync of the drbd vol.

What I would like is to have the OS drives start as /dev/sda & /dev/sdb. All others added later to the PVSCSI could be /dev/sd[c-z] or even /dev/sda[a-z] (ie /dev/sdaa /dev/sdab)

So, long story short, is there a way to either statically map SCSI devices to a particular /dev/sd* device node or at least force the LSI SCSI controller to consume device nodes first? And if possible, would this be horrible practice to do so? I have played around with some UDEV rules with little success. (Not really an expert with UDEV or even sure if this is the mechanism I should use).


Any recommendations on achieving this? Or should I just forget this and use some other method like LVM?

---

### Post by Cheesemill on 2012-05-31
> **techstig said:**
> So, long story short, is there a way to either statically map SCSI devices to a particular /dev/sd* device node or at least force the LSI SCSI controller to consume device nodes first? And if possible, would this be horrible practice to do so? I have played around with some UDEV rules with little success. (Not really an expert with UDEV or even sure if this is the mechanism I should use).


Any recommendations on achieving this? Or should I just forget this and use some other method like LVM?

I'm not sure that this is possible, it's why UUID's were invented in the first place.

I've worked with physical machines before where sd[abc] used to swap randomly on every boot, even without any drives being added or removed from the system (I think it turned out to be different rated capacitors on the drive PSU rails) :)

---

### Post by techstig on 2012-06-05
> **Cheesemill said:**
> I'm not sure that this is possible, it's why UUID's were invented in the first place.


That's what I kinda figured. But was just checking...

For what I was trying to accomplish I ended up using LVM... It actually makes more sense to use it instead of what I was trying to do. If nothing else it makes it easier to extend a LUN for DRBD (and thus iSCSI) as well as giving me a solid device name to use in LCMC. 

Thanks for the advice!

---

