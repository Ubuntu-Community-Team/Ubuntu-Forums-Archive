---
title: "GPT Partitions Limitation (Not partition size)"
date: 2010-12-13
forum: Server Platforms
---

### Post by revresxunil on 2010-12-13
Hello.

I am currently finishing up a project for my company using Ubuntu Server 10.10 on dell r610s connected to Promise Technologies SAS storage solutions.

I have two arrays that are 42.0TB large (/dev/sdb, /dev/sdc).  I am using parted to make 2TB partitions that will be used with enterprise open ISCSI and logged in by our VMware infrastructure ESX hosts to create a VMFS extentable volume (large stitched up datastore).

On one of the arrays, I have successfully parted 10 x 2TB partitions to the system, and they show up in /dev as device nodes (sdb1, sdb2, sdb3, etc).  ESX has 20TB at its disposal (yay!)

Today, I carved the remaining space on the first array and had a total of 21 x ~2TB partitions.  I read somewhere that GPT supports up to 128 total partitions in its table.  For me, however, it seems the limitation is 16 partitions.  All of my parted partitions above 16 do not have /dev device nodes (sdb17, sdb18, etc).


Since I had another array at my disposal, I carved its entire 42TB of available space into 2TB chunks like I did with the first array.  I took a look at the device nodes, and the same thing happened:  first 16 partitions show up as device nodes, the remaining are nowhere to be seen.

I have multiple resolution points for this, none of which keep the array at 42TBs.  I am wondering if anybody else has experienced this "limitation", or if it is true that Ubuntu can only do 16 partitions per device?

---

### Post by oldfred on 2010-12-13
I put gpt on my 160GB drive just to learn about it. So I cannot  help much on your size drives.

Did you use gdisk?

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by revresxunil on 2010-12-13
gdisk shows all 21 partitions correctly



I have not yet partitioned with gdisk to see if it might write the GPT partition table differently.  I will give that a try.

---

### Post by oldfred on 2010-12-13
I only respond to PM's in threads, but you might politely ask srs5694 for assistance. He is often on this forum and I think he looks for those with issues on gpt. He may pop in some anyway since your title has gpt in it.

---

### Post by revresxunil on 2010-12-14
I erased my GPT table and recreated it with gdisk.  gdisk is much more friendly in terms of partitioning, but still results in 16 of the 20 partitions showing up as device nodes.

Since I have not heard anyone else experiencing this problem, I'm going to resolve it by breaking the array in half to avoid the sweet 16.

---

### Post by Vegan on 2010-12-14
GPT can use huge partitions, do not worry about it.

If you have a 4U machine with 16 bays, using 2 TB disks you get 32 TB of raw space and 28 TB of RAID 6 storage.

Bigger disks are coming or are available for $$$$

You could have a 28 TB partition with ext4 and share it with SAMBA for Windows clients or NFS for other clients.

---

### Post by revresxunil on 2010-12-14
Unfortunately for me, I am creating a Vmware VMFS datastore, which is limited to 2TB extents.  Therefore, I must limit my partition size to 2TB - 512 bytes.

---

### Post by srs5694 on 2010-12-14
I just did a test, and I created 22 500 MiB partitions on a USB flash drive. They all show up fine under both Ubuntu 10.10 and Gentoo:

```
ls /dev/sdb*
/dev/sdb    /dev/sdb12  /dev/sdb16  /dev/sdb2   /dev/sdb3  /dev/sdb7
/dev/sdb1   /dev/sdb13  /dev/sdb17  /dev/sdb20  /dev/sdb4  /dev/sdb8
/dev/sdb10  /dev/sdb14  /dev/sdb18  /dev/sdb21  /dev/sdb5  /dev/sdb9
/dev/sdb11  /dev/sdb15  /dev/sdb19  /dev/sdb22  /dev/sdb6

```

I'm not sure why you're having problems, but my suspicion is it's something to do with the way udev is creating device nodes. Perhaps there's a bug that limits the number of partition nodes that udev creates for "real" hard disks, vs. USB flash drives. (As far as Linux is concerned, your hardware RAID setup is just a regular hard disk.) Certainly it's not a GPT issue per se. You're correct that GPT supports up to 128 partitions by default. That default value can be changed, although it's only "legal" to increase it. (It *can* be decreased by GPT fdisk, and this seems to work fine with every OS I've tried, but it violates the specifications. Increasing the limit is fine, although some versions of libparted-based tools flake out with such setups.) In any event, if the limit were decreased to 16 partitions in the partition table structures, you wouldn't be able to create more than 16 partitions with gdisk (or anything else), so that's definitely not the source of the problem.

---

### Post by revresxunil on 2010-12-14
srs5694,

Thanks for the reply.  I appreciate your time with the test, as it provides a piece to my puzzle.  

I am now under the assumption that the problem lies in the kernel, at which point I would rather break up the array, than make any changes to the stable kernel I'm using.

The fact that I can create more than 16 partitions using parted and gdisk shows clearly its not a GPT problem.

---

### Post by srs5694 on 2010-12-15
I wouldn't blame the kernel. Offhand, I don't know of any kernel options that affect this issue, and my own tests with Ubuntu used the distribution's standard kernel, while my Gentoo test was with a stock kernel (from kernel.org) that I compiled myself, so unless you've recompiled your kernel and messed with an option I don't know about, it's not likely to be the kernel.

In modern Linux systems, device nodes are created by the udev utility, so that's the likely source of the problem. Given that we both used Ubuntu 10.10 systems (albeit probably slightly different variants), my guess is that there's a bug in Ubuntu's udev configuration that only manifests for internal drives, or perhaps only when a drive is detected during the boot process (vs. later on).

---

### Post by Cosma on 2010-12-15
i don't have a solution for your partition problem but i too created a iSCSI target server for a vmware cluster not too long ago and i just put the whole raid volume into a lvm pv and created 2TB logical volumes for the iSCSI targets.

is there a reason that you didn't use lvm (performance or something else)?

---

### Post by revresxunil on 2010-12-15
Cosma,

That is something I didn't consider.  It does sound like it would eliminate the problem I have with udev by relying on the LVM subsystem, but this would add another layer of abstraction to my datastore.

I am essentially creating a large datastore for my DBA so he can create ASM partitions for oracle at his leisure, without the need for a sys admin to carve it.

I also think Redhat when I think LVM, and I really dont like Redhat that much :)


Right now my datastore is Physical Disks Array -> Logical Drive Array -> Multipath -> Many GPT Partitions -> iSCSI Targets -> VMFS datastore

With LVM, it would be Physical Disks Array -> Logical Drive Array -> Multipath -> 1 GPT Partition -> LVM -> many LVM Partitions -> iSCSI Targets -> VMFS datastore.


The abstraction with LVM wouldn't hurt performance, but it would ruin my documentation :-D


Thanks for the tip on LVM, I might consider using LVM for my second datastore and not split up its logical drive array (which will save me 2 parity disks at raid 6).

Good stuff!  Thanks guys!

---

### Post by Cosma on 2010-12-16
> **revresxunil said:**
> 
With LVM, it would be Physical Disks Array -> Logical Drive Array -> Multipath -> **1 GPT Partition** -> LVM -> many LVM Partitions -> iSCSI Targets -> VMFS datastore.


you don't need a partition at all if you use the whole disk as pv  ;)

---

### Post by revresxunil on 2010-12-16
Ubuntu community = :)

---

### Post by psusi on 2010-12-16
It actually sounds to me like it is your kernel.  There was a kernel knob you set when compiling it for how many bits of the device number to allocate to the disk, and how many to the partition.  It sounds like you only have 4 bits for the partition so you can not have more than 16 partitions.

I would suggest you use LVM for such an installation.  It is FAR more flexible than any partition table.

---

### Post by srs5694 on 2010-12-16
Psusi,

I don't recall any such kernel option, although I do have a foggy memory of an option, probably in udev, that's vaguely similar. It enables udev to assign non-standard device numbers to a device if the standard device numbers run out. Something like that is clearly going on in my case:

```
ls -l /dev/sdb*
brw-rw---- 1 root disk   8, 16 Dec 16 15:51 /dev/sdb
brw-rw---- 1 root disk   8, 17 Dec 16 15:51 /dev/sdb1
brw-rw---- 1 root disk   8, 26 Dec 16 15:51 /dev/sdb10
brw-rw---- 1 root disk   8, 27 Dec 16 15:51 /dev/sdb11
brw-rw---- 1 root disk   8, 28 Dec 16 15:51 /dev/sdb12
brw-rw---- 1 root disk   8, 29 Dec 16 15:51 /dev/sdb13
brw-rw---- 1 root disk   8, 30 Dec 16 15:51 /dev/sdb14
brw-rw---- 1 root disk   8, 31 Dec 16 15:51 /dev/sdb15
brw-rw---- 1 root disk 259,  0 Dec 16 15:51 /dev/sdb16
brw-rw---- 1 root disk 259,  1 Dec 16 15:51 /dev/sdb17
brw-rw---- 1 root disk 259,  2 Dec 16 15:51 /dev/sdb18
brw-rw---- 1 root disk 259,  3 Dec 16 15:51 /dev/sdb19
brw-rw---- 1 root disk   8, 18 Dec 16 15:51 /dev/sdb2
brw-rw---- 1 root disk 259,  4 Dec 16 15:51 /dev/sdb20
brw-rw---- 1 root disk 259,  5 Dec 16 15:51 /dev/sdb21
brw-rw---- 1 root disk 259,  6 Dec 16 15:51 /dev/sdb22
brw-rw---- 1 root disk   8, 19 Dec 16 15:51 /dev/sdb3
brw-rw---- 1 root disk   8, 20 Dec 16 15:51 /dev/sdb4
brw-rw---- 1 root disk   8, 21 Dec 16 15:51 /dev/sdb5
brw-rw---- 1 root disk   8, 22 Dec 16 15:51 /dev/sdb6
brw-rw---- 1 root disk   8, 23 Dec 16 15:51 /dev/sdb7
brw-rw---- 1 root disk   8, 24 Dec 16 15:51 /dev/sdb8
brw-rw---- 1 root disk   8, 25 Dec 16 15:51 /dev/sdb9

```

Note that partitions up to #15 have major number 8 and minor numbers 17-31; but with /dev/sdb16, the major number jumps to 259 and minor numbering shifts to 0 and up.

It's true that there are underlying kernel limits, and Cosma's issue seems to relate to these. (See the /usr/src/linux/Documentation/devices.txt file for details.) That said, one of udev's design goals was to overcome these limits on systems with huge numbers of devices. If that's not working, it's therefore a udev issue.

---

