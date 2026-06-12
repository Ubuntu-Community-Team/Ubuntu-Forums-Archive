---
title: "RAID 5 install"
date: 2009-12-25
forum: Server Platforms
---

### Post by omsoni on 2009-12-25
I bought a Dell PowerEdge T110 with 3 hard disks (160 GB each). I installed Ubuntu 9.10 Server and LAMP on it. I want to configure RAID 5 on it. If I create partition on all 3 disks, Will I loose my server installation. How can I add all 3 disk to RAID array ?

I am new to Linux. All help is appreciated.

Thanks,

Sunny

---

### Post by mhanson on 2009-12-30
Yes, you will loose all data in the process of setting up the raid array.

However, you can image your partitions with the current install on them, then make the array then place the partitions from your image onto the array. 

Dont forget to image your MBR.

Not too complicated but do your homework if you dont want to loose data.

---

