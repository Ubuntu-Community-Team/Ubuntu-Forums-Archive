---
title: "IDE RAID on Dell PowerEdge 650"
date: 2008-06-04
forum: Server Platforms
---

### Post by thumger on 2008-06-04
Hi, I'm trying to install Ubuntu Server 8.04 on a PowerEdge 650. During the install, no disks are found and I'm presented with a list of drivers to load manually. I've tried many of them, including MegaRAID.* and aacraid - but no joy.

The box has two IDE disks setup as RAID1. During boot-up the controller is shown as: PERC/CERC ATA100/4ch

'lspci' shows the card as "RAID bus controller: American Megatrends Inc. MegaRAID (rev02)".

Before I dump the RAID controller and plug the two disks into the onboard IDE controller (and use s/w RAID), any ideas on how to get RAID the card working?

Thanks.

---

