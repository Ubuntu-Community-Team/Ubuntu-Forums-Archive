---
title: "To RAID or not to RAID?"
date: 2011-02-25
forum: Server Platforms
---

### Post by FCarlo on 2011-02-25
Hi,
I am using software RAID in Ubuntu Server Edition 9.10 to mirror(RAID1) two 1TB harddrives. These are used for data storage and websites.I also have a 80GB harddrive for the operatigsystem. This drive has no backup or RAID at all. Should this drive crash and the system therefore to become no longer bootable, will I be able to recover the data the 1TB drives or should I backup the 80GB drive as well?
thanks,
FCarlo:(:confused:

---

### Post by YesWeCan on 2011-02-25
I think you should be able to assemble and mount the existing RAID from any Ubuntu instance, for example using a live CD/USB. Easy to test this.

It would save you a lot of grief in the event of a failure to make your OS disk RAID 1 too. Regular backups are always a good idea.

---

### Post by rubylaser on 2011-02-25
Yes, this is one of the great benefits of mdadm.  You could throw those disks in an linux distro with mdadm installed, and assemble the array, and have access to your media.  RAID1 on your OS is nice if you have an extra disk and don't mind the extra wattage running another disk is going to draw.

---

### Post by FCarlo on 2011-02-25
Thanks! This helps me allot!!!:P:guitar::lolflag:;):o:D

---

