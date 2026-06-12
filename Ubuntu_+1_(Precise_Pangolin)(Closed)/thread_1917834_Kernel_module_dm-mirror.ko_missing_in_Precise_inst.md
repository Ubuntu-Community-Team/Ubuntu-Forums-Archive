---
title: "Kernel module dm-mirror.ko missing in Precise installer"
date: 2012-01-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fno on 2012-01-30
I’ve been trying to install Precise onto a Intel motherboard raid (DQ67EP), and while it works great on fedora core 16, I have been struggling with both 11.10 and Precise (several builds).

It seems like the installer media (for server, alternate and netinst) is missing dm-mirror.ko.

Booting the installer goes well, configuring network and "loading additional components”. But, after entering the setup information and it’s getting time to partition the disks, full stop ahead…

I get the “Detect disks” screen, where the installer tells me that it has found one or more drives containing Serial ATA RAID configurations and asks me whether I want to activate the devices. Answering yes on this question is all that should be needed for targeting the RAID for install, right? 

Well, answering yes leads to the “Partition disks” screen, where no disks are listed, the only option is to configure iSCSI volumes. Going back, exiting to a shell:

~ #dmraid -ay
ERROR: device-mapper target type “mirror” is not in the kernel
RAID set “isw_bgidbehbc_Volume0” was not activated

As I’ve understood, dmraid needs the dm-mirror.ko in order to mount the Intel RAID volume, and this seems to not be included in the installer.

In the /lib/modules/linuxversion-generic/kernel/drivers/md directory, the following modules are included:
dm-crypt.ko dm-zero.ko faulty.ko linear.ko multipath.ko raid0.ko raid1.ko raid10.ko raid456.ko

I unpacked the initrd and copied the module dm-mirror.ko and its dependencies to the md directory and packed it. 

Booting with the new initrd and activating the Intel RAID now actually works and the installer shows the disks/volumes in the partition screen, but hangs on the purple screen after selecting the RAID volume.

1. Is it by design/choice the dm-mirror.ko isn't included?
2. Isn't Ubuntu supposed to support installing onto FakeRAIDs?

---

