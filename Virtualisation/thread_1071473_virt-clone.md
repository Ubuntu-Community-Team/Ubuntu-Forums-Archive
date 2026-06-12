---
title: "virt-clone"
date: 2009-02-16
forum: Virtualisation
---

### Post by novice buntu on 2009-02-16
Hi,

I am trying to create a clone of a guest machine I managed to created. When I run 
sudo virt-clone -d -o myquest -n guest-01 -f/var/media/myfile.img --connect=qemu:///system

I get: 
Mon, 16 Feb 2009 12:52:13 DEBUG    setup_clone in
Mon, 16 Feb 2009 12:52:13 DEBUG    clone device list: ['/var/media/myfile.img']
Mon, 16 Feb 2009 12:52:13 DEBUG    clone device size: [0]
Mon, 16 Feb 2009 12:52:13 DEBUG    clone device type: [True]
 ERROR:  list index out of range

I have seen a bug report at 
[https://bugzilla.redhat.com/show_bug.cgi?id=480253](https://bugzilla.redhat.com/show_bug.cgi?id=480253)

but that refers to the Python gui so I don't think it applies in this case.
Has anyone encountered this problem? Is there some other means that I can take a copy of the guest so I can run it on a different host?

Thanx,
Dp.

---

### Post by the_unforgiven on 2009-02-16
> **novice buntu said:**
> Hi,

I am trying to create a clone of a guest machine I managed to created. When I run 
sudo virt-clone -d -o myquest -n guest-01 -f/var/media/myfile.img --connect=qemu:///system

I get: 
Mon, 16 Feb 2009 12:52:13 DEBUG    setup_clone in
Mon, 16 Feb 2009 12:52:13 DEBUG    clone device list: ['/var/media/myfile.img']
Mon, 16 Feb 2009 12:52:13 DEBUG    clone device size: [0]
Mon, 16 Feb 2009 12:52:13 DEBUG    clone device type: [True]
 ERROR:  list index out of range

I have seen a bug report at 
[https://bugzilla.redhat.com/show_bug.cgi?id=480253](https://bugzilla.redhat.com/show_bug.cgi?id=480253)

but that refers to the Python gui so I don't think it applies in this case.
Has anyone encountered this problem? Is there some other means that I can take a copy of the guest so I can run it on a different host?

Thanx,
Dp.
You could just copy the image file to the other host and create a new VM with it. The only thing you'll miss is the XML configuration which specifies settings like network settings (bridge, mac address etc), memory allocated etc.
If you don't mind re-creating them, you can just copy the image and create a new VM with it. AFAIK, none of these settings are stored in the image file; so, it should be able to pick up the new settings during boot on the other host.

HTH ;)

---

### Post by novice buntu on 2009-02-16
Do you mean the image file as specified by the '-f' flag? There is no file created, as a result of the command. I was expecting a image file that I could import with VMWare or similar.

If you mean take a raw dump of the disk volume the guest resides on, with something like partition manager, I guess that's an option.

Thanx,
Dp.

---

### Post by the_unforgiven on 2009-02-16
> **novice buntu said:**
> Do you mean the image file as specified by the '-f' flag? There is no file created, as a result of the command. I was expecting a image file that I could import with VMWare or similar.
No, I meant the original VM image file - the one you're using to boot into the VM already - the one you're trying to clone.

Are you using a disk partition to boot the VM?
You can check it up in the XML configuration file of the VM - unfortunately, I've forgotten the path at which you can find this XML :(

You can also see the machine details from virt-manager - which is a GUI frontend for libvirt-supported hypervisors.

> **novice buntu said:**
> 
If you mean take a raw dump of the disk volume the guest resides on, with something like partition manager, I guess that's an option.

Thanx,
Dp.
Taking the dump of the physical volume won't help - you need to get at the VM disk image file - unless you're booting the VM off the physical volume/partition.

---

### Post by novice buntu on 2009-02-17
> Are you using a disk partition to boot the VM?

Yes it's an LVM Volume?

I can't seem to mount it on the host machine. The volume is craved up by the guest into 3 partitions. So when I do


```
mount -t ext3 /dev/mapper/VolOne-myguest /mnt
```  

I get 
>  VFS: Can't find ext3 filesystem on dev dm-0.

So I'm not sure how to proceed. I notice there are some updates for libvirt-bin which I am going to install now. Fingers crossed these will fix the problem with virt-clone.

---

### Post by novice buntu on 2009-02-17
Unfortunately not
> 
Tue, 17 Feb 2009 10:11:36 DEBUG    clone device size: [0, 0]
Tue, 17 Feb 2009 10:11:36 DEBUG    clone device type: [True, True]
 ERROR:  list index out of range


---

### Post by the_unforgiven on 2009-02-17
> **novice buntu said:**
> Yes it's an LVM Volume?

I can't seem to mount it on the host machine. The volume is craved up by the guest into 3 partitions. So when I do


```
mount -t ext3 /dev/mapper/VolOne-myguest /mnt
```  

I get 


So I'm not sure how to proceed. I notice there are some updates for libvirt-bin which I am going to install now. Fingers crossed these will fix the problem with virt-clone.
Well, in this case, I don't think virt-clone can help.
And since the LVM volume has already been clobbered by the VM by creating partitions *inside* it, you cannot hope to mount it on the host either.

However, you can dump the partition into a file which can then serve as the disk image for your VM.

You can use dd to dump the volume into a file:
```
dd if=/dev/mapper/VolOne-myguest of=/path/to/image/file
```
For more details on how to use dd, check its manpage.

Once this image file is created, you can even loop-mount it onto host.

---

### Post by novice buntu on 2009-02-17
Is using LVM not a goos idea then you want to create VM guests? Should I just crave up the drive(s) in the extended volume as I need the (boot, swap, root) for each guest.

---

### Post by the_unforgiven on 2009-02-17
> **novice buntu said:**
> Is using LVM not a goos idea then you want to create VM guests? Should I just crave up the drive(s) in the extended volume as I need the (boot, swap, root) for each guest.
Not really..
Essentially, as long as you keep the meaning of the storage same between guest and host (if it's LVM volume, let it be an LVM volume in the guest as well), there shouldn't be problems.

What has happened in your case is that host thinks that it's an LVM volume and expects to find the filesystem in it when you try to mount it. But, since you've created partitions *inside* the LV from within the guest, the FS layout and the structures are *one level below*.

The easiest setup for a VM is just to create a file in the host filesystem that is used as an emulated disk for the VM. This creates least amount of hassles and even if something goes wrong with this file (say, partition table getting corrupted), you can just delete the file and create a new one. The host doesn't get affected. Inside the guest, it's treated as though it's a plain blank HDD and you can create whatever layout you want inside it - LVM, normal DOS partitions, whatever.

When you share physical disk storage (say, LV or a partition), if the guest happens to mess it up, chances are that your host OS will also be affected because of the clobbered partition table.

HTH ;)

---

### Post by novice buntu on 2009-02-17
That has helped. Thanx. 

I wonder if, by creating my VM to use a partition and not a disk file, it has lead to these errors from virt-clone.

---

### Post by bonnieuehh1 on 2011-01-14
> **novice buntu said:**
> Hi,I am trying to create a clone of a guest machine I managed to created. When I run sudo virt-clone -d -o myquest -n guest-01 -f/var/media/myfile.img --connect=qemu:///systemI get: Mon, 16 Feb 2009 12:52:13 DEBUG setup_clone inMon, 16 Feb 2009 12:52:13 DEBUG clone device list: ['/var/media/myfile.img]Mon, 16 Feb 2009 12:52:13 DEBUG clone device size: [0]Mon, 16 Feb 2009 12:52:13 DEBUG clone [[COLOR=#000000]device[/COLOR]](http://www.rersoft.com/m4v-files/convert-m4v-to-3gp.html) type: [True]ERROR: list index out of rangeI have seen a bug report at [https://bugzilla.redhat.com/show_bug.cgi?id=480253](https://bugzilla.redhat.com/show_bug.cgi?id=480253)but that refers to the Python gui so I don't think it applies in this case.Has anyone encountered this problem? Is there some other means that I can take a copy of the guest so I can run it on a different host?Thanx,Dp.Nice writing, It is just the solution for my problem, Thanks for your effort! Now I understand more about it.

---

