---
title: "Automount encrypted volume with keyfile only?"
date: 2010-05-14
forum: Security
---

### Post by AntiMattR on 2010-05-14
Hi all.

I have built a new NAS device and I would like for the storage drives to be encrypted  and have it boot from a flash device which can automatically mount the disks with a keyfile.  Since I intend for it to be headless, an appliance basically, I want to be able to insert the flash device, power it up and then have it bring up the shares; ready to be mounted on machines on the network.  Without the flash device the NAS is unbootable and the data is secure.

Right now I am using the newest Ubuntu Server and booting it from a high-speed CF card is pretty quick and I am happy with that, I just want to know the best way to have the storage drives to automount.

The storage drives (in RAID1) are currently without a filesystem so I am open to using whatever encryption package is ideal (TrueCrypt, LUX, etc).  I want to get this all set up before I start copying data onto it.

Thanks a lot!

---

