---
title: "lvm ontop of raid10 or combine two raid1 via lvm?"
date: 2009-09-09
forum: Server Platforms
---

### Post by Okar on 2009-09-09
hi,
I'm planning to setup a ubuntu file server. I'll be using the 8.04LTS server edition.

the system is probably going to have 4 harddrives.
at the end they shall form an software RAID10 system.

I'd like to use lvm at some point in order to able to make snapshots

as I read through some mdadm and lvm docu/tutorials I could think of two possible setups:

in both cases:
small raid1 of 2 partitions that will form /boot
small raid1 of 2 different partitions as swap space

1.
the rest will form 2 large raid1, which will be combined to a single virtual drive via lvm

2.
make a raid10 out of the rest with mdadm, then make a lvm volume group just consisting of the 1 virtual raid0 device

are there pros/cons for either solution?
is lvm as powerfull as mdadm in striping?
will the first solution produce less overhead?

---

