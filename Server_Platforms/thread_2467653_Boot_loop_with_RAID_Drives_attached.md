---
title: "Boot loop with RAID Drives attached"
date: 2021-10-03
forum: Server Platforms
---

### Post by JusticeEmpire on 2021-10-03
Hi All,
Making an attempt to get my server up and running again, (HP ProLiant box) and I've managed to get the OS to boot up and run from its on HDD, but this is only when the 4x RAID Drive caddies are removed. When they are installed, I get stuck in a boot loop with this error - Non system disk error, or no disk error

I've done all sorts of things to try and get the server to work, it is probably VERY messed up. I've tried to reinstall OS, with no luck, I don't know what to look for in terms of mdadm and fstab, I've formatted the RAID drives to ext4 to try and disable the RAIDs to see if it would with them attached, but no joy. 

The only thing I can think of now is to replace the OS HDD and start again....unless there is something super obvious that someone here with more knowledge than me can point out?

Thanks in advance

---

### Post by TheFu on 2021-10-03
When either mdadm or the older, dmraid, RAID were used, they'd modify an area of the disk to say "this is part of a RAID set."  I think mdadm has a command to clear that.  [https://serverfault.com/questions/488346/removing-raid-metadata-from-drives](https://serverfault.com/questions/488346/removing-raid-metadata-from-drives) You probably already did that.

As for getting any HP to work, that's a difficult issue, since HP is known to do odd things in their BIOS and motherboard designs.  The different versions of the DL380 servers each have different Linux support challenges.  I recall fighting and failing to get a Gen3 to run with a 5 yr newer Ubuntu Release.  The DL380 Gen3 was on the official "supported Ubuntu hardware list" ... at the time it was current hardware for an LTS release.

After clearing the RAID flags, check the exact model and version of the HP system to see whether anyone else already solved the install of 20.04 server issue.  Today, that is the only release someone running server should install.

You may need to go into the RAID-card BIOS and set it into JBOD mode. Be certain to use AHCI, not RAID.  
[https://community.hpe.com/t5/ProLiant-Servers-ML-DL-SL/Cannot-install-Ubuntu-12-04-on-HP-Proliant-DL380e-with-1TB-SAS/td-p/6147559](https://community.hpe.com/t5/ProLiant-Servers-ML-DL-SL/Cannot-install-Ubuntu-12-04-on-HP-Proliant-DL380e-with-1TB-SAS/td-p/6147559) has some commands that might be helpful.  Probably not, but it can't hurt. Answers will be very specific to the model, generation and RAID controller.

---

