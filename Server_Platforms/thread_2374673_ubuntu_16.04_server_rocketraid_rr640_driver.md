---
title: "ubuntu 16.04 server rocketraid rr640 driver"
date: 2017-10-18
forum: Server Platforms
---

### Post by bmcclint2 on 2017-10-18
Anyone has success with this card on 16.04 server?


I am upgrading an old 12.04 server which has been using this card/driver for year without fail.  I can get the driver to compile following all the suggested methods and I can even install the 1.0 version I had on 12.04.  The driver will load and will initialize all the disks.  Note that I am not using it as a raid controller at this time I am attempting to build a zfs raidz2.  I can get the zfs array up and running but as soon as I start copying files within a minute or two I get io errors and drives drop out.  All the drop outs are random devices on the rr640 card.  So I am not buying that the drives have suddenly gone bad but maybe.


Just so its clear the setup.


Ubuntu 16.04 Server
RR640 w/ 4x2TB WD Reds
On the main board I have 2x2TB hitachi drives but the geometry is the same.


Old setup was RR640 w/ 4x2TB into a RAID5.  Onboard 2x2TB were mirrored and critical data from RADI5 was copied and mirrored.


New setup intention is RR640 w/ 4x2TB + Onboard 2x2TB into ZFS Raidz2 using all six disks.  Setup seems to work just intermittent errors.


Confused...

---

### Post by wildmanne39 on 2017-10-18
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

