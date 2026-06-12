---
title: "Moving luks encrypted raid 1 to new machine"
date: 2009-08-01
forum: Security
---

### Post by nunki on 2009-08-01
I am going to be setting up a luks encrypted software RAID 1 on my ubuntu machine. I want to make sure I cover all my bases and understand how to move it to another computer in the future.

I've read up about how to move a software RAID array to a new computer, but I need to know if the fact that it is encrypted will cause any issues.

The reason I want to know this is because my computer is getting older, and I want to make sure when its time to get a new one that transferring the array will be easy. 

Is it as easy as ```
mdadm --assemble --scan
``` then create a crypttab entry, fstab entry and then mount the array?

---

