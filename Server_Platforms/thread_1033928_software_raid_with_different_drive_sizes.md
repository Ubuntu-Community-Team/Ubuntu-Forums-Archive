---
title: "software raid with different drive sizes?"
date: 2009-01-07
forum: Server Platforms
---

### Post by Mouth on 2009-01-07
Hi,
I have a 8.04 dedicated server with 2 drives of different sizes; 80Gb and 320Gb. Ubuntu and data is all on the 80Gb drive, with the 320Gb drive to be used for holding backups.

Is it possible for me to partition the 320Gb drive into a 1 x 80Gb partition and 1 x 240Gb partition and use software raid for mirroring the 80Gb drive onto the 80GB partition of the 320Gb drive? If so, URL pointers please? My google's only led me to raid of same size drives.

I then intend to use the 240Gb partition of the 320Gb drive to store staged full/incremental backups of essential data (mysql/www) etc.

Thanks.

---

### Post by windependence on 2009-01-07
Yes, you could do this, and the raid IS the same size as you are using the same size partition as your drive. Just create the partition, format it as a RAID volume and raid it with your other drive. You will need to create a small non-RAID boot partition on the primary drive because you can't boot from a software RAID volume.

-Tim

---

### Post by fjgaude on 2009-01-07
> **Mouth said:**
> Hi,
I have a 8.04 dedicated server with 2 drives of different sizes; 80Gb and 320Gb. Ubuntu and data is all on the 80Gb drive, with the 320Gb drive to be used for holding backups.

Is it possible for me to partition the 320Gb drive into a 1 x 80Gb partition and 1 x 240Gb partition and use software raid for mirroring the 80Gb drive onto the 80GB partition of the 320Gb drive? If so, URL pointers please? My google's only led me to raid of same size drives.

I then intend to use the 240Gb partition of the 320Gb drive to store staged full/incremental backups of essential data (mysql/www) etc.

Thanks.

What you wish to do is done sometimes. You use raid1 under mdadm for the pair of partitions, and a normal partition for what's left over on the big drive.

This link should help you get your bearing about raid1, booting from such:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)  

Let us know how you are doing.

---

### Post by Cracauer on 2009-01-09
I do that all the time. I also have more raids involving different/less disks on the leftover partitions of the bigger disks.

---

