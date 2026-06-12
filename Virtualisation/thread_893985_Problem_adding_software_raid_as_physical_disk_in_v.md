---
title: "Problem adding software raid as physical disk in vmware"
date: 2008-08-18
forum: Virtualisation
---

### Post by slackey on 2008-08-18
I have 3 physical disks in my system. Sda contains my Ubuntu Server install, acting as the host OS for VMWare. Sdb and sdc are set up in a software raid 0 as device md0. I want to use md0 as a physical disk so one vm can use the entire raid volume as its disk. The problem is, when I try to add a physical disk during the virtual machine creation process, all that shows up is /dev/sda, /dev/sdb, and /dev/sdc. Does anyone know why /dev/md0 isn't showing up?

---

### Post by fjgaude on 2008-08-19
I've not known anyone using software raid in a VM... the issue is that VMware has to recognize the array as a device and then to immulate it. Not sure if vmware has such a capability.

Anyone know?

---

### Post by PilotJLR on 2008-08-19
Raw Device Mapping to software raid isn't supported in VMware Server.

What you need to do is mount /dev/md0 to some mount point on your host, then make a new vmdk virtual disk in the Server Console, and present that vmdk to the guest.

---

### Post by erielf on 2008-10-01
PilotJLR,

How can I mount a host-directory in a vmware guest?

Could you explain what to do after mounting the raid-device?
I click on Add, and then Harddisk in the vmware console, but then what?
I can't use the physical disk option, and it's not a new disk and using an existing disk requires a vmdk-file, which I don't have...

Thanks a lot for your help!

---

### Post by PilotJLR on 2008-10-01
Sure, for a NEW virtual disk, you should be able to create a new "hard disk" in the Server console; simply store this new disk in a directory of your choosing (i.e. what local storage resource you want to use).

So, in other words, if you use the hose to mount /dev/md0 to a mountpoint like /mnt/storage/, then you would use the Server Console to make a new hard disk in the /mnt/storage/ mountpoint.

---

### Post by erielf on 2008-10-02
Thanks PilotJLR,
but what I wanted to do was to mount the raid device (or the directory) AS a hard disk in vmware, not create a harddisk-file within the raid-device.

But thanks anyway,

---

### Post by Georgi Sotirov on 2008-10-06
I also have problems with vmware - it doesn't find my SATA disk and when I enter it manually after I thy to save the virtual machine I get the error "The specified device is not a valid physical disk device". I've checked the device permissions, the partition is not mounted... I still can't find solution... I thought the the problem could be that I have only one disk and few partitions are already mounted by Linux, but your post disprove my assumption.

---

