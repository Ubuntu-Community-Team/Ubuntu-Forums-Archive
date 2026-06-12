---
title: "Boot VM from External Hard Drive"
date: 2016-01-23
forum: Virtualisation
---

### Post by bigpappajohn1984 on 2016-01-23
I have an external hard drive that is from a dead PC.  What I would like to do is connect this drive via USB to my machine and boot it using a VM.  Is this possible in Lubuntu?  What would be the best VM to do such with?

---

### Post by ian-weisser on 2016-01-23
The VM doesn't matter. Pretty much any VM will work.
The flavor of Ubuntu doesn't matter. Pretty much any flavor of Ubuntu will work.

The hard part is that VMs are designed to use virtual drives, not real drives.
One simple method is to convert the external hard drive into a disk image, then create a virtual drive from that disk image.
The disk .img, and the .vdi may take a _lot_ of disk  space, so ensure you have available on your bootable system approx twice the external drive used space. (If the dead system occupies 30G, have at least 60G available on your live system)

Here's [one example]("https://wiki.archlinux.org/index.php/Moving_an_existing_install_into_%28or_out_of%29_a_virtual_machine#Moving_into_a_VM") of how to do it for VirtualBox.

---

### Post by bigpappajohn1984 on 2016-01-23
> **ian-weisser said:**
> 
The hard part is that VMs are designed to use virtual drives, not real drives.
One simple method is to convert the external hard drive into a disk image, then create a virtual drive from that disk image.
The disk .img, and the .vdi may take a _lot_ of disk  space, so ensure you have available on your bootable system approx twice the external drive used space. (If the dead system occupies 30G, have at least 60G available on your live system)

Here's [one example]("https://wiki.archlinux.org/index.php/Moving_an_existing_install_into_%28or_out_of%29_a_virtual_machine#Moving_into_a_VM") of how to do it for VirtualBox.

Thank you for that info, and the link.

Unfortunately after obtaining this information for my case, I do not think this will work :(.  My bootable system is a 120 GB SSD and the drive I want to use as a VM is aa 1 TB drive with roughly 160 GB used, which already exceeds the capacity of my internal drive.

---

### Post by ian-weisser on 2016-01-24
What's the goal? Recover data? Restore a favorite desktop environment? Run a specific aplication in it's tailored environment? 
Does it _need_ to be bootable? Does it need to be a VM?

---

### Post by MAFoElffen on 2016-01-25
> **ian-weisser said:**
> What's the goal? Recover data? Restore a favorite desktop environment? Run a specific application in it's tailored environment? 
Does it _need_ to be bootable? Does it need to be a VM?
That's what I was curious about... from a different perspective.

- If he does not need to "boot" from it, and just needs access to it, then he could access it from a VM as a shared Host resource... But the host, running a hypervisor (any kind of virtual machine type of software) needs to be able to recognize the file system on the drive, to be able to access from the VM through the host, as a host shared resource. So it is not possible for a Windows Host to be able to recognize and be able to share an ext4 filsesystem.

- If he does or does not need the data on it ... ? 
 -- If he needs the data, and it did not have much on it... if you resize the partitions first, then converted to an image file, then image can be stored anywhere, on any filesystem (so on any physical disk). So if he did that, and temporarily stare it on the host... Then if he had to re-org the flash dish for the host OS to be able to read, then he could store the image file back onto it. If that is his "logical" goal.

 -- if he does not need the old data on it, then it would still help performance of running a VM to stored the VM and VM images on that physical disk. You might expect performance of running a VM, with good host resources, to be able to at most, run a VM within 80-90% of running native. Most of that is disk I/O. You flash disk can store your VM images...

---

