---
title: "Faild software raid drive"
date: 2008-02-22
forum: Server Platforms
---

### Post by vtec on 2008-02-22
I have a personal server I set up about 3 years ago (mail,web,dns,routing,cvs,ect....). I remember back when I built it I used to drives to create a software RAID1. Today I received an email from the system saying that a drive has failed. The good news is it seems to be running fine right now in a degraded state. Here is the out but from mdstat:


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 dm-3[2](F) dm-2[0]
      1020032 blocks [2/1] [U_]

md0 : active raid1 dm-1[2](F) dm-0[0]
      243167744 blocks [2/1] [U_]

unused devices: <none>


So what do I do from here. Do I try to rebuild the drive with the failed disk to see if it was a one time error??? That doesn't sound like to good of an idea so I was thinking about getting 2 new drives, one to replace the failed one, and one to use as a hot spare. I'm not sure how to do this though. How do I determine what drive of the two went bad, and then what has to be done to add two new drives into the array???

---

### Post by rickyjones on 2008-02-22
> **vtec said:**
> I have a personal server I set up about 3 years ago (mail,web,dns,routing,cvs,ect....). I remember back when I built it I used to drives to create a software RAID1. Today I received an email from the system saying that a drive has failed. The good news is it seems to be running fine right now in a degraded state. Here is the out but from mdstat:


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 dm-3[2](F) dm-2[0]
      1020032 blocks [2/1] [U_]

md0 : active raid1 dm-1[2](F) dm-0[0]
      243167744 blocks [2/1] [U_]

unused devices: <none>


So what do I do from here. Do I try to rebuild the drive with the failed disk to see if it was a one time error??? That doesn't sound like to good of an idea so I was thinking about getting 2 new drives, one to replace the failed one, and one to use as a hot spare. I'm not sure how to do this though. How do I determine what drive of the two went bad, and then what has to be done to add two new drives into the array???

I believe there are some query options for mdadm that will give you details about the array - it should tell you what is missing. Figure out which drive it is, pull it out, add in the two new drives, and use mdadm to re-add the new drive. Should be fine. I've been testing the behavior in a virtual machine and it seems to work extremely well.

-Richard

---

