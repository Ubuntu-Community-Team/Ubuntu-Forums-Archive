---
title: "EXT4 16tb volume resize to 24tb wont resize via gparted."
date: 2018-09-26
forum: Virtualisation
---

### Post by oliver-whittington on 2018-09-26
Hi guys,

I have a VM that has a large disk attached to it. The drive was originally created as a 16tb volume (not using LVM) and mounted to /dev/sdb. The disk is presented to the VM via our SAN.

My question is, why can't i resize it? I've tried upping the volume to 18tb by dropping to a gparted bootable ISO and the volume dosn't allow me to grow it past 16tb?

any ideas? the volume has the 64 bit flag but strangely the version of [COLOR=#242729][FONT=Consolas]e2fsprogs  [/FONT][/COLOR]is 1.42.x as opposed to 1.43.x 

what would be a safe way of extending the volume? oh. And there's no partition table for it :S

Image -> [https://ibb.co/nqLpwp](https://ibb.co/nqLpwp)

---

### Post by howefield on 2018-09-26
Thread moved to the "*Virtualisation*" forum.

---

### Post by spjackson on 2018-09-26
Welcome to the forums.

There's no partition table for it? Have you deleted it or has it never been used and therefore contains no significant data?

Before you can create a larger partition using gparted, you need to increase the volume size using VM tools. Here's one tutorial [https://linuxhint.com/increase-virtualbox-disk-size/](https://linuxhint.com/increase-virtualbox-disk-size/)

However, if it has no data on it and it isn't the boot disk, you could just remove it from the VM and create a bigger one.

---

### Post by oliver-whittington on 2018-09-26
Hi spjackson - Thanks for the reply.

Yeah its the secondry disk and it has no partition table but does have accessible data on it. Very significant data. :) 


I have provisioned the storage on the SAN and grown the RDM in ESX but the available disk space dosnt show up.

---

### Post by TheFu on 2018-09-27
I would contact VMware for support.

ext4 shouldn't have any issues sizing to petabytes, since EB is the listed size limitation, but I've always had a partition table on my storage to ensure admins see the partition table and don't think the storage isn't being used. It prevents accidents. 

ext3 has a 16TB size limitation, however. Are you certain it is ext4?  

Have you tried **resize2fs** or **fsadm** to resize it?

---

### Post by Skaperen on 2018-10-03
_[FONT=courier new]gparted[/FONT]_ is a tool for changing partitions.  if there is no partition table, it is pointless to use _[FONT=courier new]gparted[/FONT]_ or any partitioning tool.  doing so could ***destroy*** your data.

what you need to do is re-allocate more space in the SAN while retaining  the original 16TB and adding 8TB more at the end .  i guess you have already done this step.  then you need to  verify that your guest OS can see this re-allocation as a size change.   Linux may be able to see the change without rebooting, if nothing is  using the device at the time (is not mounted).

you can verify this by viewing the contents of [FONT=courier new]/proc/partitions[/FONT] by doing the command **_[FONT=courier new]cat /proc/partitions[/FONT]_**  in a terminal.  root or sudo are not required to verify.  the output  should be a 4 column whitespace-separated list with the sevice or  partition names in column 4.  look for **[FONT=courier new]sdb[/FONT]**.  [FONT=courier new]/dev/[/FONT] is not part of the names in this list.

column  3 has the sizes in units of 1024 bytes.  below is a table various large  sizes in multiple of 1TB.  your sizes may not be exactly theses values,  but should be within about 12% either way.  i marked the sizes you will  be most interested  in.

14TB = 15032385536
15TB = 16106127360
16TB = 17179869184 <<<<
17TB = 18253611008
18TB = 19327352832
19TB = 20401094656
20TB = 21474836480
21TB = 22548578304
22TB = 23622320128
23TB = 24696061952
24TB = 25769803776 <<<<
25TB = 26843545600
26TB = 27917287424
27TB = 28991029248
28TB = 30064771072
29TB = 31138512896
30TB = 32212254720
31TB = 33285996544
32TB = 34359738368

once your VM guest Linux sees the device having the correct size then it is time to run the **_[FONT=courier new]sudo resize2fs[/FONT]_** command.  if the filesystem is currently mounted, append the mount point to the command.  if it is not mounted, append the device name to the command.

note that the device size change done by the SAN *may* not propagate to Linux while the device is busy.  being mounted makes it busy.  if you do not need to keep it mounted continuously, you can unmount it for these steps.

---

