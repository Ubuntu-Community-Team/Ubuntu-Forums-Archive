---
title: "Comparing virtualbox snapshots/images?"
date: 2009-03-16
forum: Virtualisation
---

### Post by kpatz on 2009-03-16
Just wondering if anyone has an easy way of doing this, or has any suggestions.

Let's say that I'm running XP as a guest on virtualbox.  I take a snapshot of the virtual drive.  Then, I infect it with a virus.  Now, I want to see what files the virus created/modified, by comparing the last snapshot to the current state.

Is there any way to do this?

I suppose one way is to setup another VM running a Linux distro, or even another copy of XP, and then mount the infected VM's disk images and compare them from there.  But I don't think you can mount an image minus 1 snapshot without reverting the snapshot, can you?  What would be cool is to be able to mount the image minus 1 snapshot as one read-only drive, and the image current state as another, and then do a compare from those.

I suppose another option is to clone the image rather than use snapshots, infect one image, then mount both in another VM to compare.

Thoughts?  Any easier way to do this?  A utility to view or mount Virtualbox images from the host OS would be handy for something like this.

---

### Post by HankB on 2009-03-18
I don't know if this helps or not... You may already be ahead of me on your thinking. 

I'm not aware of any way to view the virtual disk from outside the VM, so I think the key is to boot Linux in the VM - either using a live CD or dual boot installation within the VM. Once Linux is running, you can save images of the drive anywhere convenient so that you can do before and after comparisons. If you share a the Host file system with the guest, you can even copy images out of the VM for further analysis.

Since you tell VirtualBox what OS you are using when you create a VM, I would try creating a second VM that uses the same virtual disk but configured to run Linux in order to boot a live CD or dual boot to Linux.

-hank

---

### Post by kpatz on 2009-03-18
Thanks... I think you're right.

I wish VBox had more facilities for accessing images from the host.  It would make life easier.  Even a way to create/mount floppy images would be a huge time saver.  Just the other night I needed to create a DOS VM with networking for a customer (don't ask...)  There are numerous "boot floppy" utilities out on the net, but they all run in Windows and generally require you to create an actual floppy.  I was doing this on my (XP) laptop which doesn't have a floppy drive, so to create a floppy disk image to boot a VM from, I had to run XP in a VM, create and format a blank floppy image, and then run the bootdisk creator from there.

I already have Ubuntu, XP, and Win7 VMs built, so I'll just mount the drive images on one of those and use that for comparison purposes.  It's just a bit of a PITA.

---

### Post by kpatz on 2009-03-18
I figured out how to mount Virtualbox drive images in Linux.

First, the images have to be static (fixed-size).  Dynamically-allocated images won't work.

> sudo mount <path_to_vdi_file> <mountpoint> -t fs_type -o loop,offset=1024

seems to do the trick quite nicely.  I tried it with an ext3 filesystem, haven't tried it with ntfs yet, but I see no reason why it won't work.  VDI files (the static type) have a 1024-byte header followed by the image data, thus the offset=1024 on the loop does the trick.

EDIT: This only works if the image doesn't have partitions.  If it does have partitions, some math is required to figure out the offset, to set the loop device to the beginning of the partition you're trying to mount.

---

