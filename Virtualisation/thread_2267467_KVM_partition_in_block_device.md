---
title: "KVM partition in block device"
date: 2015-03-01
forum: Virtualisation
---

### Post by diego36 on 2015-03-01
Hi,

I think I've done something realy stupid now.  Years ago, I created a partition, made it ext3 and assigned it to my virtual machine (KVM).  This has its advantages and its disadvantages.  I don't want to start a discussion on that, but it is just the way it is.

Now, I've moved the partition into an LVM volume (which I didn't have at first) and now the virtual machine doesn't know the UUID of the partition any longer.  I just keep falling back to a busybox shell with the message that /dev/disk/by-uuid/XXX does not exist.  If I type 'ls /dev/disk', I don't even see a directory by-uuid.  There's only a by-id directory there.  If I type 'blkid' I see the correct ID for my partition (but maybe that's because I tried to recover by resetting it to the right uuid from within the host system).

Anyway, I just seem to be unable to get my file system mounted.  I've tried a lot of things already, but I just can't get any further.  Most stuff on fora about /dev/disk/by-uuid are about normal systems, but this doesn't work for me as I'm in this special case where I'm running in a VM and with no partition table in my VM's block device.

Anyone an idea on how I could recover my VMs?

Thx in advance,

Diego

---

### Post by redger on 2015-03-02
as a *guess*
[LIST=1]
[*]the partition has an "internal" structure which is visible to a VM, but not to the host filesystems
[*]the VM sees the host image in a very different way, possibly containing multiple "partitions" (where the host sees a single partition
[*]you've changed the UUID from the host perspective .... but not the VMs perspective
[/LIST]


have you tried this -
[LIST=1]
[*]allocate the LVM partition to another VM (as a seondary or "data" partition)
[*]start this other VM and use it's tools to mount this "data partition" so you can access /etc/fstab on the original and change the UUID setting (or change to the /dev/sdX format). You'll probably have to mount the partition first which will mean identifying it with lsblk or blkid
[/LIST]

then you should be able to stop the VM you just used to access and make the change, disconnect the LVM partition (or not, as you choose) and start the "old" VM with its now "fixed" partition

you can also use host tools to do this(though I have not tried them) , see
[LIST]
[*][http://libguestfs.org/]("http://libguestfs.org/")
[*][http://blog.vmsplice.net/2011/02/how-to-access-virtual-machine-image.html]("http://blog.vmsplice.net/2011/02/how-to-access-virtual-machine-image.html")
[*][https://wiki.archlinux.org/index.php/QEMU#Mounting_a_partition_inside_a_raw_disk_image]("https://wiki.archlinux.org/index.php/QEMU#Mounting_a_partition_inside_a_raw_disk_image")
[/LIST]

---

### Post by diego36 on 2015-03-02
Thanks redger for your reply.  I tried something similar as you suggest by starting from a live CD (over virt-viewer).  But it seems my VM just doesn't see a uuid after changing from a real partition (well, md raid0, actually) to the LVM volume.  I also mounted the VM's partition in my host system to fiddle with the fstab, I even tried changing it to /dev/sda instead of the uuid, I changed grub to ignore the uuid, etc.  But to no avail.

The strange thing is, as you say, I might have partitions within.  I do have a couple of VMs on that host and for one of them I actually do have a proper partition table in the VM partition.  And that one does start properly.  To be more precise: I have md1, md2 and md3, each holding the disk for a VM.  md1 and md3 are ext3 partitions and these are the VMs that can no longer boot.  On md2 I have a partition table (which looks in the host as md2p1, md2p2, ...  Of course, after moving this to the logical volume, I don't see this any longer, but this is the VM that still boots.  So I think something in my partition was changed by the host by the move to LVM.  As the disk that formerly was md2 has its own partition table, all its partitions still have their proper UUIDs, but those that were md1 and md3 have not.

I did roll back to the old situation now, as I still had the other raid disk safely aside.  So the system is running again, but without the LVM.  After looking into the links you suggested, and if that doesn't work, I think I'll try to create proper partition tables in md1 and md3.  I just don't know how yet.  I'll probably play around with a new partition which I can prepare with fdisk.  If I then copy the root partion with dd and install grub from within a live CD, I think it must work.

---

### Post by redger on 2015-03-02
good luck. I'm interested to hear how you go

I find it useful to have a couple of "maintenance" VMs I can attach things to for this kind of maintenance - one for Linux and one for Windows

---

### Post by diego36 on 2015-08-14
Hi Redger,

Sorry for the long silence, but this was a time-consuming task and of course I also have other things to do.  But I do want to post this here to let you know that I finally made some progress and maybe someone else might benefit.  You never know...

Anyway, I did follow your device and created a couple of test VMs on my laptop.  To make a long story short, I started playing with copying parts of image files around and in the end, this worked.  I created a small script to make dd copy small pieces at a time, from the back to the front, to make space for the partition table.  Then I found this info on how to populate my boot record: [[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)].  However, because the article was written with a physical system in mind, I had to jailroot into the mounted new partition to install the bootloader.

I had some practice now and I'm rather confident on the process.  However moving the partitions around on the disk seems rather tricky.  I intend to buy me a couple of extra disks on which I'll properly prepare the LVM volumes.  With the process I know now, I can then copy the current partitions into the new logical volumes, taking the right amounts of space into account.  This way, once all my VMs are on the new disks, I can remove the partitions on the old disks and add the newly available space to the volume group.

Anyway, thanks for the ideas that pointed me into the right direction.

Regards,

Diego

---

### Post by redger on 2015-08-14
well done, I'm glad it worked out :)

---

