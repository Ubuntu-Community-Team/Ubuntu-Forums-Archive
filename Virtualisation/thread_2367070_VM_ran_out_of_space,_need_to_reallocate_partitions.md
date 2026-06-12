---
title: "VM ran out of space, need to reallocate partitions"
date: 2017-07-25
forum: Virtualisation
---

### Post by andrew_davis2 on 2017-07-25
Hello, 

I have a VM that I built using VMWarePlayer I ran out of space on my machine's partition '/dev/sda1'.  I expanded the VM using the VMWare tools and got a warning that says I need to examine the partitions.

I started up the machine using the ISO and opened up 'GPartEd' but cannot seem to get the new 30GB I added to the machine associated with the '/dev/sda1' partition.  

I'm pretty new at all of this with regards to the partitioning of a Linux box (I just let the defaults run on VMWarePlayer).  Any help would be welcome.

Andy

[ATTACH=CONFIG]276134[/ATTACH]

---

### Post by deadflowr on 2017-07-25
Moved to *Virtualization*

---

### Post by TheFu on 2017-07-25
Think of storage you add via VMware Player as adding a physical disk.  If you don't use LVM, I don't know of away to merge 2 physical disks into a single logical volume (a fancy "partition").

It isn't clear.  Do you want to 
a) keep the old and add the new 
or are you willing to 
b) do a fresh install onto the new, using LVM, then move all the data from the old disk into the new LVM, and then wipe the old disk, convert it into LVM storage and extend the PVs, VGs, and LVs to share both virtual HDDs
c) or do you want the easiest answer to have 60G total storage and just add a new 60 virtual HDD and completely clone the existing sda into sdb, then resize the partitions.

There are 50 other methods, BTW.

I see the "unallocated" storage in your image. How is it connected to the VM?  SATA, virtio, IDE? 

Seems the OS doesn't know what to make of it.  **It should have a device path like /dev/sdb** - then you should partition it and format it.  Then you can use whatever method you like to migrate the sda stuff over to sdb (do it running a live-CD like the Gparted one you are using already).

I've never used Player, so cannot really help.  We stopped using VMware and Oracle stuff, switching 100% to KVM/virt-manager around 2011. Never regretted doing that.

---

### Post by andrew_davis2 on 2017-07-26
Thanks for the reply, 

This whole thing was predicated by my building a database and it growing to a point where the vm disc could not hold it anymore.  

I thought that by expanding the disc I was 'growing' my storage capacity, didnt know I would have to do anything else until the warning. 
Yes, I like the idea of having 60gb of total storage and then cloning the existing into the new container.  As far as resizing the partitions, it would be nice to understand how that is done.

The 50 does not surprise me.. I have much to learn.

I created that unallocated storage through the tools with VMWare Player, it does not specify a connection for it.  Looking at the choices you've named, I am going to guess 'virtio' or some type of similar mechanism.  

So out of the options you named, I would like to do 'C'....

Andy.

---

### Post by TheFu on 2017-07-26
I should have mentioned this too.  Sometimes I'm blinded by too many options. ;)

'C' is the better choice.  I should have used it when I needed to add more storage to my VMs.  I had blinders on and because I use LVM, merging storage isn't hard.

Every other virtualization suite has a method to expand/resize storage volumes if you use their storage container (vdi, vmdk, qcow2, whatever).  Have you researched that?  Just don't do it when the VM is running/active.

I use KVM/QEMU - it has a tool **qemu-img** which is used to modify or convert storage that isn't just a passthru (passing through an LVM LV is common).  It can probably resize the vmdk storage too.  From the manpage (you do know about manpages, right?):

```
QEMU-IMG(1)                                                        QEMU-IMG(1)

NAME
       qemu-img - QEMU disk image utility

SYNOPSIS
       usage: qemu-img command [command options]
...
       resize [-q] filename [+ | -]size
...
       resize filename [+ | -]size
           Change the disk image as if it had been created with size.

           Before using this command to shrink a disk image, you MUST use file
           system and partitioning tools inside the VM to reduce allocated
           file systems and partition sizes accordingly.  Failure to do so
           will result in data loss!

           [B]After using this command to grow a disk image, you must use file
           system and partitioning tools inside the VM to actually begin using
           the new space on the device[/B].
```

Anyway, the point is that I strongly believe that VMware Player will have a tool like that even if resize isn't part of the GUI.  I know Xen does. I know virtualbox does.  I know VMware ESX does.

Worst case, you can use qemu-img - I checked. It supports vmdk storage (and a bunch of others).  The last paragraph above (bold) is part of what I was trying to explain in my initial post.  Everything done at the VM layer (outside the VM guest OS) really just looks like moving hardware around.  Definitely use the VMware-made tool, if you can.

Lastly, I'm still at a loss for why the new disk you added wasn't showing up as /dev/sdb inside gparted. It should have. My only guess is that it wasn't properly connected to the VM with a disk controller (that would be virtual too, BTW).

Hope this makes sense.

---

### Post by andrew_davis2 on 2017-08-01
Thanks.. again.  Your information helped me.  It turns out I also found a blog with print screens of part of the process here.
[http://blog.mwpreston.net/2012/06/22/expanding-a-linux-disk-with-gparted-and-getting-swap-out-of-the-way/](http://blog.mwpreston.net/2012/06/22/expanding-a-linux-disk-with-gparted-and-getting-swap-out-of-the-way/)

---

### Post by TheFu on 2017-08-01
Please mark the thread "SOLVED" to help others in the community.

---

