---
title: "root lvm unable to increase in vmware"
date: 2012-05-27
forum: Server Platforms
---

### Post by whiteB on 2012-05-27
Hi,

We are using UBUNTU8.04 as web servers, deployed in Vmware ESX4i.

Currently / parition was 100% and tried to add one more vmdisk and added to the / VG..But while expanding, it is showing error..and the filesytem got corrupted..

Kindly give any suggestions..

---

### Post by LHammonds on 2012-05-27
Well, if it is corrupted, you are going to have to boot with a Live CD (use the same version that your OS is using) and repair the damage.  This has to be done while the partition is unmounted...hence the need to boot from CD.

I would then suggest looking at what you can delete to free up a bit of working room.

Then fdisk the new HD, pvcreate the HD, add the physicial volume to the logical volume group, then expand the root logical volume and finally expand the root file system.

Check my sig for a link to how I setup a mysql server and look at the Volume Management section for details on those commands.

LHammonds

---

