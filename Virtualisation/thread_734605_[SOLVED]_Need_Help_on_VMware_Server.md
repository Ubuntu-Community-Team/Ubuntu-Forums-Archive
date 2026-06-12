---
title: "[SOLVED] Need Help on VMware Server"
date: 2008-03-24
forum: Virtualisation
---

### Post by enofman on 2008-03-24
Ok I think I'm at wits end.  I have tried to install VMware both as a virtual drive and a physical drive.  I have a 300GB SATA drive and a 20GB IDE drive. I have Ubuntu on the 300 with 8GB for the / and the rest for the /home.  Which is probably not the way to configure, but being GREEN.  I would like to use the /home for a virtual drive area.  However when I try to configure a virtual guest VMware tells me there is only 3.6GB left which is what is on the / partition.  Is there a way to force VMware to look at the /home partition or should I change the partition.  If, not then how can I change the ownership and permissions for my IDE drive to run the Virtual guest off the physical drive.  I keep getting Unable to complete wizard: insufficient permission to access file.  Please remember I am extremely new. I appreciate all help.

Thanks Gary

I sat for awhile took a break and got the physical drive to accept.  Had to use gksudo vmware, probably read it somewhere and it didn't sink in until I took a break.
Thanks anyway.

---

