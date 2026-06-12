---
title: "Raid1?"
date: 2014-02-22
forum: Server Platforms
---

### Post by Edward_Collinson on 2014-02-22
Hey, I'm new :P.
That asside, I am having a problem with the Hp Proliant Microserver N40L Raid configs, I don't know how to make Ubuntu 12.04 pick up the Logical disk :(.

I have a raid1 config with disks 3-4 and a logical disk is appearing in the configs, but ubuntu sees the two disks and not the logical one?

Any Ideas?

~Ed

P.S, I have ubuntu not-raided on the primary disk.

---

### Post by SeijiSensei on 2014-02-22
Is the RAID array constructed using software RAID in Linux?  You would have used the mdadm command for this.

Some "RAID" controllers require additional software drivers to make them work.  That software is usually available for Windows but not Linux.  If you want to create a RAID device, use [Linux software RAID]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html").

---

### Post by Edward_Collinson on 2014-02-23
No, the raid software is the "fakeraid" that comes with the Hp proliant Microserver, 
Thanks for your help. I will just use the software raid that linux has :)

---

