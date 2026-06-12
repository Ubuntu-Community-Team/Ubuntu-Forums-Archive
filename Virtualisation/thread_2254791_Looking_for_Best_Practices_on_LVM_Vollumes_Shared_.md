---
title: "Looking for Best Practices on LVM Vollumes Shared between Host and Guest"
date: 2014-11-30
forum: Virtualisation
---

### Post by FreeFog on 2014-11-30
HI!!!!!!!!!!!
I want to create a VirtualBox machine inside my Kubuntu 14.04, it will run Windows 7 64Bits.
The machine will have two drives, Boot (128MB) and C (48GB).
I want the drives to be LVM (Linux Logical Volume Manager) manageable and that both the Host and Guest can access them simultaneously with out causing corruption, even while the VM is running.
I mainly intend to have the Host PC to be in charge of syncing the entire VM to a cloud account and the direct access to the disk is a bonus. I want the cloud service to be able to read the state of every file.

Q1 - I'm open to many suggestions, I will continue to show what I tried and how it failed:

MAP

Host Name = THEHOST
Kubuntu 14.04
[INDENT]Partition Table
[/INDENT]
[INDENT=2]_Type        = GPT
[/INDENT]
[INDENT=2]_Location    = sda
[/INDENT]
[INDENT]sda1 = efi
sda2 = Kubuntu
sda3
[/INDENT]
[INDENT=2]_Size        = 100Gb
_Format    = Unpartitioned
_Flags      = lvm
[/INDENT]
[INDENT]sda4 = swap[/INDENT]
LVM:

vgPC1[INDENT]lvBoot
[/INDENT]
[INDENT]lvC
[/INDENT]

Guest Name = PC1

Tried formatting sda3 to ext4 but I am fonder of leaving it unformulated and flagged lvm.

Try1 - Using two LVs and running mkfs from the host. Then give RAW Access to the guess thru:
VBoxManage internalcommands createrawvmdk -filename PC1_Boot.vmdk -rawdisk /dev/vgPC1/lvBoot
VBoxManage internalcommands createrawvmdk -filename PC1_C.vmdk -rawdisk /dev/vgPC1/lvC
Then adding them to the VirtualBox machine.
Result:
The Guest can't see the drives.

Try2 - Using two LVs with RAW access as described in Try1 and using Windows 7's installation partitioning tool.
Result:
When I access and modify anything thru the Host the changes are desynced with what it is made by the Guest, generally requiring to reboot the system to see some or part of the changes.

Try3 - Created one big LV and formatted using W7 Installation.
Result:
To access the internal partitions I have to do extra mappings with kpartx, the mappings can be created on boot but the doc says it would not adapt to lvm changes automatically. Haven't done enough testing about the file sync.


Q2 - Is there a way to use RAW Partition access?
Q3 - Should I use kpartx?, manual says it is insensitive to changes.
Q4 - I'm worried what would happen if I modify the LVs while using RAW Disk access , Would I need to update the VirtualBox Raw access files?
Q5 - Would the same apply (Q4) if using RAW Partition access?

Thanks for your Time.

---

### Post by bashiergui on 2014-11-30
First make sure the host is 64 bit so it can run a 64 bit guest. If Kubuntu is 32 bit then you'll need to do some extra work to get a 64 bit guest running. You can find more details in the virtualbox documentation.

If it's just data you're trying to share you might consider shared folders. A Windows guest will map the shared folder as a drive.

---

### Post by FreeFog on 2014-11-30
But that would rely on a virtual network, and might cause problems with system files? The idea is to put the entire VM in a cloud account so the cloud software will need access to everything.

Yes 64x Host for a 64x PC.

Yes I been reading VirtualBox and Xen Docs.

Thanks.

---

### Post by bashiergui on 2014-11-30
So you don't want to share data, you want to share system files. Name some of the common system files between Windows and Kubuntu.

---

### Post by FreeFog on 2014-11-30
You mean 2 NTFS filesystems inside 1 or 2 LVM vollumes over an unformated sda3 and Ext4 for the host OS partition or do u mean anything else?

---

### Post by bashiergui on 2014-11-30
I've never tried it but I found this tutorial, sounds like it is not straightforward in Virtualbox.
[http://mobile.serverwatch.com/server-tutorials/using-a-physical-hard-drive-with-a-virtualbox-vm.html](http://mobile.serverwatch.com/server-tutorials/using-a-physical-hard-drive-with-a-virtualbox-vm.html)

It does caution you that you cannot mount a physical drive that is in use by the host OS. So I'm not sure you can accomplish what you want. This seems like a question better put to the Virtualbox forums.

---

