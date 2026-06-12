---
title: "adding new RAID1 array"
date: 2009-09-21
forum: Server Platforms
---

### Post by upstatelabs on 2009-09-21
I am new to linux.  I've installed ubuntu server 9.04 as the OS on a HW RAID1 array.

I added a second RAID1 array to the system, but I don't know how to make the OS recognize, format, and mount the new array.  Can someone point me in the right direction, as the guides I've read so far haven't been that much help in this area?

Thanks much!

---

### Post by Lars Noodén on 2009-09-21
If it is all configured and hardware raid, it should look like a single disk to the operating system.  If it does, then partition it, create file systems on the partitions, set mount points and options, and them mount them. 

Try (carefully) the tool gparted if you want a GUI for doing most of that.

---

### Post by upstatelabs on 2009-09-21
> **Lars Noodén said:**
> If it is all configured and hardware raid, it should look like a single disk to the operating system.  If it does, then partition it, create file systems on the partitions, set mount points and options, and them mount them. 

Try (carefully) the tool gparted if you want a GUI for doing most of that.

Thanks!  One more question...
For a primary disk, I would have to worry about a root and probably a swap partition.  Can I partition the whole second array as one big ext3 "data" partition, or is there anything else I should be considering?

---

### Post by trundlenut on 2009-09-21
> **upstatelabs said:**
> Thanks!  One more question...
For a primary disk, I would have to worry about a root and probably a swap partition.  Can I partition the whole second array as one big ext3 "data" partition, or is there anything else I should be considering?

Yes, that is exactly what I did.  You need a mount point for your new partition, I chose /storage on my server.

---

