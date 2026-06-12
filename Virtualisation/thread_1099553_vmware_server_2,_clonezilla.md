---
title: "vmware server 2, clonezilla"
date: 2009-03-18
forum: Virtualisation
---

### Post by roscowgo on 2009-03-18
Hello all,

I have an elderly windows server, running 2000 server that I would like to virtualize.   It has 2 scsi disks, multiple partitions across those two disks, and a usb drive I'd prefer to have as a virtual device as well.

Can I use clonezilla to create images of these disks, create an appropriate virtual machine with the right number/size of disks, and use clonezilla to "restore" to that now virtual device?

Or is there some easier way that I don't know about being a N00b and all?

I'm worried about making the virtual device as close to identical as possible, as it is still accessed by users looking up data in quite a few scanned documents.   Thus the clonezilla.   It's also an AD controller.

---

### Post by bodhi.zazen on 2009-03-18
I doubt your strategy will work easily as windows will complain that the hardware has changed.

I suggest you back up your files and data, anywhere you like, and install windows 2000 in a VM (fresh install) then transfer the data.

Otherwise follow a how to :

[http://4sysops.com/archives/p2v-for-vmware-six-ways-to-convert-physical-to-virtual/](http://4sysops.com/archives/p2v-for-vmware-six-ways-to-convert-physical-to-virtual/)

---

