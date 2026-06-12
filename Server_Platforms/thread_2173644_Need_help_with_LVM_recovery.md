---
title: "Need help with LVM recovery"
date: 2013-09-10
forum: Server Platforms
---

### Post by netwise on 2013-09-10
Hi 

I need some information on how LVM works. To start off let me explain my situation.
I had an older redhat system that was storing some old archive backups. The system consisted out of  two drives in a LVM2 Volume set.

The first disk had 2 partitions.

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63      208844      104391   83  Linux
		(100mb Boot Partition)
Partition 1 does not start on physical sector boundary.
/dev/sdc2          208845  2930272064  1465031610   8e  Linux LVM
Partition 2 does not start on physical sector boundary.

The second disk had only 1 LVM partition

For some reason something when wrong with the ext3 filesystem and the system stopped booting.
I suspect that one of the drives are slightly dodgy. As it turns out this was only discovered once we realized we need some of the data off the old backups. To be belt and braces I thought it best to rather clone both disk to new disk before I attempt a recover as I'm no Linux Expert and would probably need a few goes at it.

And this is where I stuffed things up badly for myself.

To clone the disks I connected them to my ubuntu system with two new 2TB disks. I installed ddrescue. But when I started my first clone I made a mistake in identifying which drive is which.

I ended up coping 800Mb (821 515 KB ) of the first disk over the beginning of the second disk. Before this happened I was able to see the VolumeGroup in ubuntu but of course after a reboot the system now thinks that disk one and disk two are the same disk even though only the beginning of the drives have been overwritten.

How do I now go about recovering my LVM.
For now I've disconnected disk one and only connected disk 2 (the overwritten disk) running a pvscan yields the following


Found duplicate PV x1Yg3zsd2YJAzjo22vTs02S9jAbaj1mX: using /dev/sdc2
  Couldn't find device with uuid p8yKhC-7t70-kSti-Cz7A-WznH-94lZ-Aj6GAp.
  PV unknown device   VG VolGroup00   lvm2 [1,36 TiB / 0    free]
  PV /dev/sdc2        VG VolGroup00   lvm2 [1,36 TiB / 0    free]
  Total: 2 [2,73 TiB] / in use: 2 [2,73 TiB] / in no VG: 0 [0   ]

Any guidance in how to reassemble this would be appreciated.

Thank You

---

### Post by LHammonds on 2013-09-12
> **netwise said:**
> I need some information on how LVM works.
I don't have time to go through you post fully (need to leave work) but I have how-to documentation on how to setup LVM, backup and restore in my signature link (setup ubuntu)

I hope it helps clarify LVM for you.

---

