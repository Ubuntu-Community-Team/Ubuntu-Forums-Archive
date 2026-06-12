---
title: "Installing RAID 10 fresh install 10.10 64bit server on a Supermicro 6025B-T"
date: 2011-03-17
forum: Server Platforms
---

### Post by toyota_f1 on 2011-03-17
I have a client with a pair of Supermicro 6025B-T servers that he wants to have Ubuntu 10.10 64bit Server running on for VM/Cloud experimenting.  He needs these to be set up RAID 10.  I can go into the Adaptec utility and make the array and make it bootable and get to the point in the installer where it asks me if I want to use the SATA array - then it gets to the partitioning screen and the array is nowhere to be found.

Any help would be appreciated.

Thanks!

Isaac

---

### Post by psusi on 2011-03-17
That is a fakeraid card.  Fakeraid is less well supported than conventional linux software raid, so you should avoid it.  Destroy the array in the bios utility, then setup an mdadm software raid array when you install.  See [http://wiki.ubuntu.com/FakeRaidHowto](http://wiki.ubuntu.com/FakeRaidHowto) for more info.

---

