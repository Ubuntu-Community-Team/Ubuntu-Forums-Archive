---
title: "Ubuntu Server 10.10 Broken Partition table in raid 5 setup with MDADM"
date: 2011-12-11
forum: Server Platforms
---

### Post by sauce345 on 2011-12-11
Set up:
Ubuntu 10.10 Server
1 80 GB system drive
5 1TB in Raid 5 with mdadm

I had a drive fail in my raid array and when I tried to replace it I just accidently erased a partition on a functioning disk in my raid array thinking it was the new drive I put in.  

I was having the hardest time figuring which physical drive had failed but when I determined the bad drive and put the new drive in all the drive letters changed.  So me being a confident idiot thinking I new the right drive /dev/sdf and made a new partition on to prep it for addition to the raid array.  Remember at this point I only had 4 of 5 drives still operational so the array was still in tact.

After I burned one of the four remaining drives it reports that the raid is active and still functioning but it throws errors when you try to mount it.

Is their any way to restore a partition table? or somehow copy one of the other still functioning drives partition table to this one so I don't loose any of my data? I am freaking out here cause raid 5 totally served its purpose here and I just being the moron I am screwed everything up potentially loosing TB's of data.

:(

---

### Post by ian dobson on 2011-12-11
Hi,

Just use fdisk to recreate the partition table _exactly_ the same size as the one you deleted. fdisk just updates the partition tables without changing anything else.

Note, this will only work if you haven't modified the actual data on the disk.

Regards
Ian Dobson

---

### Post by sauce345 on 2011-12-12
Thanks for your reply, I will give that a try.

I saw somewhere else on the net the command sfdisk and its ability to copy partition tables.  Do you think it would also work to just copy the partition table from one of the remaining good drives to the  faulty drive?  I just don't remember exactly how I created the partions on the raid drives because it was like 2 years ago.

Else I will try to figure out what it should be and set it as how you recomended.  Thanks for the tips!

---

