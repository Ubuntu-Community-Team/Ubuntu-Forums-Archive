---
title: "Clean install and an existing separate LV/RAID drive"
date: 2014-08-26
forum: Server Platforms
---

### Post by roger61 on 2014-08-26
Apologies if this is a daft question, but a straight answer (which I haven't yet found) could save a lot of server downtime!

I have a server with 11.04 and I want to perform a clean install of 14.04 on a new replacement HDD for /root. The old system also has a /data drive, which is a separate pair of HDDs with a LV on top of RAID1, all healthy. 

My question is: what will I need to do (if anything) to "install" the /data drives on the new system so they are recognised at boot and are mountable? All the old config files will be available from a backup if necessary.

---

### Post by TheFu on 2014-08-26
Step 1 before every major update is to make a know-you-can-restore/recovery backup. I'd start there before doing anything.

Your RAID hardware probably isn't the same as mine.
Your LVM setup probably isn't the same as mine.

I have migrated softRAID arrays from system to system without any more trouble than just having to mount to RAID devices. The RAID arrays have moved from system to system and from 10.04 to 14.04 - fresh OS install.  That machine doesn't have LVM.

For an LVM migration, I'd definitely vgexport and do a vgimport. Wouldn't expect any issue, but ... things don't always work out.

---

