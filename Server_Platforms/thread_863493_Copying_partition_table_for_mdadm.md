---
title: "Copying partition table for mdadm"
date: 2008-07-18
forum: Server Platforms
---

### Post by breadlord on 2008-07-18
Hi,

I've been running a RAID 5 array using mdadm for about 18 months now, and one of the drives has recently died, I've removed it just fine, but now I need to replace it. I'm currently using 300 gig drives that don't seem to be available anymore. What's the best way of copying the partition table / filesystem information from one of the working discs to a new, larger one, so I can rebuild the array?

I'm aware I'll have a bunch of unused space at the end of the new one, that's not a problem...

---

### Post by pdwerryhouse on 2008-07-18
sfdisk can do it:

```
sfdisk -d /dev/hda > /tmp/hda.pt
```

You can then write this to the new disk with:

```
sfdisk /dev/hdX < /tmp/hda.pt  
```

(It might be wise to fix the device names in the file first before writing it to the new disk, although I don't know if this is strictly necessary. Hopefully sfdisk is smart enough to know what you're doing).

Now, all that said, I don't think you need to match partition sizes within the new device. As long as all of your RAID5 partitions are bigger than their matching partners in the existing disks, mdadm will only use the amount of space that it needs within each. This might actually make it easier for you in the long run, if the other disks fail and you need to replace those...

---

### Post by breadlord on 2008-07-19
Ahhhh, so I could increase the size of my array by getting a new set of discs, replacing each in turn and rebuilding? If that's true then me not installing LVM (Because I'm thick...) might not be as much of a problem as I thought...

---

### Post by pdwerryhouse on 2008-07-19
Yeah, I'm not actually sure what will happen there. Haven't ever tried it myself, so I don't know how it handles the case where all the slices have grown. Might be worth testing it under vmware first ;)

---

### Post by fjgaude on 2008-07-21
I've built raid5 arrays with drives as different as 36 to 500GB... mdadm works with the 36 for all drives... it shows a caution message and then lets you proceed. Very nice!

---

