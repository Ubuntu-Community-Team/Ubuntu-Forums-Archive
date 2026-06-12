---
title: "Upgrade from 10.04 to 12.04 via cd?"
date: 2012-08-02
forum: Server Platforms
---

### Post by xkaliburx on 2012-08-02
Well the subject states it pretty well.  We have a pretty standard 10.04LTS server and I need/want to upgrade to 12.04LTS.  I am burning the CD now and will be headed out to the co-lo later today.

I haven't seen any issues but should I expect any problems upgrading via CD.  I don't want to go the dist-upgrade to 11, then 11.10, etc. so are there any known issues.

There is no X installed, all packages (apache, etc.) are the binary installs.

Tnx

---

### Post by Cheesemill on 2012-08-02
You *should* be fine.

Just make sure you have a full backup to roll back to if there are any problems.

---

### Post by xkaliburx on 2012-08-02
Yep, actually going to image via clonezilla and do have a data backup, these servers are so self sufficient, I rarely do upgrades unless it's a need, and this is a PCI requirement.

I knew a seasoned admin would answer quick  :)

Tnx

---

### Post by gordintoronto on 2012-08-02
> **xkaliburx said:**
> Well the subject states it pretty well.  We have a pretty standard 10.04LTS server and I need/want to upgrade to 12.04LTS.  I am burning the CD now and will be headed out to the co-lo later today.

I haven't seen any issues but should I expect any problems upgrading via CD.  I don't want to go the dist-upgrade to 11, then 11.10, etc. so are there any known issues.

There is no X installed, all packages (apache, etc.) are the binary installs.

Tnx

You can dist-upgrade from LTS to LTS. I'm no fan of that approach; I always do a clean install.

---

### Post by xkaliburx on 2012-08-02
Thanks I dropped of the CD booted and left to come home.  As it stands, there is no 'upgrade' so need a little more research.  The GUI starts, jumps to network, then name, and next comes partitioning the device.

I can look at the partition setup but it states 'hey were gonna wipe all this, etc.' and didn't see any 'dont format' type, so I rebooted for now, left the CD in place, and rebooted, selected boot from hard drive, so at least it's back in production while I figure out what my next move is.

Tnx

---

### Post by xkaliburx on 2012-08-03
ok still keeping that CD in there, right off the root of the disk there is an 'cdupgrade' shell script you can run which it's doing now.

Sad there was no mention on the autostart, etc. but luckily the reading was the key.  Figured I would post it here to both close and in case someone else needed it know  :)

Tnx again for the replies

---

