---
title: "VMware ESXi and Ubuntu 8.04 Buffer I/O errors"
date: 2008-10-27
forum: Virtualisation
---

### Post by JGillTech on 2008-10-27
I have about 14 virtual machines within my ESXi infrastructure, split between Windows and Linux.  I am having an issues with Ubuntu distributions and buffer I/O errors.  I noticed this problem when I migrated a 6.06 LTS installation over to ESXi.  The file system would change to read-only after an unknown amount of time.  I tossed it up to a failed transfer and then built a new server with Ubuntu 8.04 LTS.  After a week or so, same errors.  This time I have some console errors:  Buffer I/O error on device sda1, logical block 3619427.  Eventually the file system is mounted in read-only mode.  A few days after I deployed the first 8.04 server, I deployed another.  When I checked the 2nd 8.04 virtual machine, I saw the same results.   Any idea?

---

